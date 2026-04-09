# 🤖 E-commerce Backend API v1.1 - Advanced AI & Analytics

This document extends the core documentation with high-end features including AI specialized modules, deep user trust systems, and administrative "Mission Control" dashboards.

---

## 🤖 1. AI Intelligent Modules (`/ai`)

These endpoints leverage specialized AI models to provide a premium, modern shopping experience.

### A. AI Visual Search
Search for products using an actual image rather than text.
- **Endpoint:** `POST /ai/visual-search`
- **Request Format:** `Multipart/Form-Data`
- **Field Name:** `image` (Type: File)
- **Response Format:**
```json
{
  "success": true,
  "data": [
    { 
      "productId": "65f1...", 
      "matchScore": 0.98, 
      "productDetails": { "name": "...", "price": 4999, "images": [...] } 
    }
  ]
}
```

### B. Conversational Shopping Assistant
Talk to our AI to find exactly what you need.
- **Endpoint:** `POST /ai/assistant`
- **Body:** `{ "message": "I need red running shoes for men under 5000" }`
- **Response Format:**
```json
{
  "success": true,
  "reply": "I found 3 great options for you. The Nike Air Max is highly recommended!",
  "suggestedProducts": [ ...productObjects ],
  "intent": "search_shoes"
}
```

### C. AI Review Analysis
A "TL;DR" summary of all user reviews for a specific product.
- **Endpoint:** `GET /ai/product/:id/summary`
- **Response Format:**
```json
{
  "success": true,
  "summary": "Most users love the comfort, but suggest ordering half a size larger.",
  "sentimentScore": 4.5,
  "pros": ["Comfort", "Breathable"],
  "cons": ["Sizing runs small"]
}
```

---

## 👤 2. Enhanced User Profile & Trust (`/user`)

### A. Address Book Management
| Method | Endpoint | Description |
| :--- | :--- | :--- |
| GET | `/user/addresses` | List all saved addresses |
| POST | `/user/addresses` | Add: `{ street, city, state, zipCode, country, isDefault }` |
| PUT | `/user/addresses/:id` | Update specific address |
| DELETE | `/user/addresses/:id` | Remove address |

### B. Product Review System
- **Endpoint:** `POST /products/:id/reviews`
- **Body:** `{ "rating": 5, "comment": "Amazing quality!" }`
- **Logic:** Updates the product's `averageRating` and `numReviews` automatically.

### C. Persistent Wishlist (Verification)
- **Endpoint:** `POST /user/wishlist/toggle/:productId`
- **Description:** One-click toggle. Adds if missing, removes if present.

---

## 📊 3. Admin "Mission Control" Dashboards (`/admin`)

Full analytics suite for business growth.

### A. Revenue Analytics (TimeSeries)
- **Endpoint:** `GET /admin/analytics/revenue`
- **Query Params:** `?period=daily|weekly|monthly`
- **Response:** Array of `{ date, total }` objects for graph charting.

### B. Hot-Selling Products
- **Endpoint:** `GET /admin/analytics/top-products`
- **Description:** Returns top 5-10 products filtered by sales volume.

### C. Bulk Inventory Tool
- **Endpoint:** `POST /admin/products/bulk-upload`
- **Body:** `[ {product1}, {product2}, ... ]` (JSON Array)
- **Use Case:** Initial data migration or massive stock updates.

---

## 🛡️ 4. System Improvements & Standards

### A. Advanced Product Filtering (Updated)
The `GET /products` endpoint now supports full logic:
- **Pagination:** `?page=1&limit=20`
- **Price Range:** `?minPrice=500&maxPrice=5000`
- **Search:** `?q=searchterm` (supports AI natural language)
- **Sorting:** `?sort=price` (asc) or `?sort=-price` (desc)

### B. Real-time Webhooks
We now support standard polling and are ready for **Socket.io** integration for real-time order tracking:
- `Status: Shipped`
- `Status: Out for Delivery`

---
> [!IMPORTANT]
> All endpoints require `Authorization: Bearer <token>` in the header for secure access.

**Prepared by Antigravity Senior Architecture Team.**
