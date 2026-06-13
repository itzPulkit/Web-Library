# 🔌 AI-Powered Digital Library API & Service Specification

This document outlines the complete API architecture, local service configurations, and external **free tier** APIs required to make the project fully operational in a real-world production environment.

---

## 🌐 1. Third-Party & Free Tier APIs

To keep operational costs at zero while deploying a high-performance system, the project will utilize the following developer-friendly free APIs:

### A. Core AI & LLM Engine (Chatbot, Summaries, Auto-Tagging)
*   **Provider:** **Google AI Studio (Gemini API)**
    *   **Service:** Gemini 2.5 Flash / Gemini 1.5 Flash
    *   **Free Tier Allowances:** 15 Requests Per Minute (RPM), 1,500 Requests Per Day (RPD).
    *   **Use Cases:** RAG virtual librarian assistant, generating book summaries, analyzing reader feedback for sentiment, and extracting keywords/tags.
    *   **Docs:** [Gemini API Documentation](https://ai.google.dev/gemini-api/docs)

### B. Book Metadata & Cover Asset Finder
*   **Provider:** **Open Library API (by Internet Archive)**
    *   **Service:** REST API & Covers API
    *   **Free Tier Allowances:** 100% Free, Open, and requires no API key.
    *   **Use Cases:** Fetching book details (publisher, release year, summaries, categories) and standard cover image URLs via ISBN or title.
    *   **Docs:** [Open Library Developer Portal](https://openlibrary.org/dev/docs/api/)
*   **Alternative Provider:** **Google Books API**
    *   **Free Tier Allowances:** Generous free queries per day. Excellent for search autocomplete and retrieving missing metadata.

### C. Asset Storage (Book Covers & PDF Manuscripts)
*   **Provider:** **Cloudinary**
    *   **Service:** Cloud Media Asset Management
    *   **Free Tier Allowances:** 25 Monthly Credits (~25 GB of storage / bandwidth, or 25,000 image transformations).
    *   **Use Cases:** Uploading and optimizing user avatars, writer-submitted book cover files, and reading PDFs.
    *   **Docs:** [Cloudinary Free Plan Details](https://cloudinary.com/)
*   **Alternative Provider:** **Supabase Storage**
    *   **Free Tier Allowances:** 1 GB of S3-compatible storage & 5 GB bandwidth.

### D. Plagiarism Screening Engine
*   **Provider:** **Local Vector Comparison (100% Free)**
    *   **Service:** Sentence Transformers (`all-MiniLM-L6-v2` running in python-backend memory) + Cosine Similarity.
    *   **Cost:** Completely Free (runs on host cpu/memory).
    *   **Use Cases:** Scanning uploaded writer manuscripts against the existing library database using embedding cosine similarity scores.

### E. Backend Hosting & Database
*   **Provider:** **Supabase / Neon.tech**
    *   **Service:** Managed serverless PostgreSQL.
    *   **Free Tier Allowances:** Supabase offers 2 free projects; Neon offers 1 project with 0.5 GiB of storage.
*   **Provider:** **Render**
    *   **Service:** Web Services (FastAPI hosting) & Static Site Hosting (React frontend).
    *   **Free Tier Allowances:** Free web services (spin down after 15 mins of inactivity).

---

## 🔑 2. Internal Backend API Endpoints (FastAPI)

The FastAPI backend will expose the following REST endpoints to the React frontend.

### A. Authentication Module (`/api/auth`)
| HTTP Method | Endpoint | Description | Access Role | Request Body | Response JSON |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `POST` | `/register` | Register a new account | Guest | `{ username, email, password, role }` | `{ id, username, email, role, token }` |
| `POST` | `/login` | Authenticate and obtain JWT token | Guest | `{ email, password }` | `{ access_token, token_type, user_info }` |
| `GET` | `/me` | Get active user profile and wallet balance | Reader/Writer/Admin | *None* | `{ id, username, email, role, points_balance }` |

### B. Library Management Module (`/api/books`)
| HTTP Method | Endpoint | Description | Access Role | Request Parameters | Response JSON |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `GET` | `/` | Retrieve paginated books sorted by categories | Guest / Reader | `page, limit, category` | `[ { id, title, author, category, cover_url } ]` |
| `GET` | `/search` | Natural language **semantic search** | Guest / Reader | `query` (e.g. "books about AI logic") | `[ { id, title, score, summary } ]` |
| `GET` | `/{id}` | Get complete book details & user reviews | Guest / Reader | `id` (path) | `{ id, title, author, summary, reviews: [] }` |
| `POST` | `/` | Create a new book entry (manual upload) | Admin / Writer | `{ title, author, category, description, cover_url }` | `{ success: true, book_id }` |
| `DELETE` | `/{id}` | Remove a book listing from database | Admin | `id` (path) | `{ success: true, message }` |

### C. Borrowing Records Module (`/api/borrow`)
| HTTP Method | Endpoint | Description | Access Role | Request Body | Response JSON |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `POST` | `/request` | Borrow a digital library book | Reader | `{ book_id }` | `{ transaction_id, due_date, status: "borrowed" }` |
| `POST` | `/return` | Return a borrowed library book | Reader | `{ transaction_id }` | `{ success: true, return_date, points_earned }` |
| `GET` | `/active` | List user's currently borrowed items | Reader | *None* | `[ { transaction_id, book_title, due_date } ]` |

### D. AI Chatbot Agent (`/api/chatbot`)
| HTTP Method | Endpoint | Description | Access Role | Request Body | Response JSON |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `POST` | `/chat` | Submit query to the RAG Virtual Librarian | Reader / Writer | `{ message, history: [] }` | `{ reply, suggested_books: [ { id, title } ] }` |

### E. Writer Portal & Plagiarism Check (`/api/publishing`)
| HTTP Method | Endpoint | Description | Access Role | Request Body / Multipart | Response JSON |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `POST` | `/upload` | Upload manuscript file (PDF / DOCX) | Writer | File upload, `{ title, genre_guess }` | `{ file_url, processed_words, tag_suggestions }` |
| `POST` | `/plagiarism-scan` | Run similarity index check on manuscript | Writer | `{ file_url }` | `{ similarity_score, matches: [ { book_id, title, match_percentage } ] }` |
| `POST` | `/auto-classify` | Generate AI summary & tags via Gemini API | Writer | `{ file_url }` | `{ summary, tags: [], suggested_category }` |

### F. Reader Feedback Marketplace (`/api/marketplace`)
| HTTP Method | Endpoint | Description | Access Role | Request Body | Response JSON |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `POST` | `/gigs` | Create a feedback request offering points reward | Writer | `{ book_id, reward_amount, criteria }` | `{ gig_id, status: "active" }` |
| `GET` | `/gigs` | List available feedback reward tasks | Reader | *None* | `[ { gig_id, book_title, reward_amount, criteria } ]` |
| `POST` | `/submit-review` | Submit detailed, multi-paragraph review | Reader | `{ gig_id, review_text, rating }` | `{ review_id, status: "pending_verification" }` |
| `POST` | `/verify` | LLM automatically rates feedback quality | Writer / System | `{ review_id }` | `{ quality_rating, sentiment, points_awarded }` |

---

## 🔒 3. Environment Variable Requirements (`.env`)

To configure access to local and remote services, create a backend `.env` containing:

```env
# Database Settings
DATABASE_URL=postgresql://user:password@localhost:5432/bookstore

# JWT Authentication Config
JWT_SECRET=supersecretjwtkeychangeinproduction
JWT_ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=1440

# Third-Party AI Keys
GEMINI_API_KEY=AIzaSyYourGeminiApiKeyHere

# Third-Party Asset Storages
CLOUDINARY_URL=cloudinary://api_key:api_secret@cloud_name
```
