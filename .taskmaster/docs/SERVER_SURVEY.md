# 🖥️ SERVER/BACKEND FEATURE SURVEY

**Purpose:** Understand your exact requirements for the blog backend features.  
**Instructions:** Please answer each question clearly. Add notes/explanations where helpful.

---

## 📋 SECTION 1: PROJECT OVERVIEW

### 1.1 Project Vision

**Q1.1:** What's the primary goal of this blog?

- [ ] Personal tech blog / portfolio
- [ ] Content marketing / business blog
- [ ] Community / multi-author platform
- [x] Other: \_Personal blog but have multiple topic, like tech, social, art, music, sharing....**\*\***\_\_**\*\***

**Q1.2:** Expected scale in first year?

- [x] < 100 posts, < 1K monthly visitors
- [ ] 100-500 posts, 1K-10K monthly visitors
- [ ] 500+ posts, 10K+ monthly visitors
- [ ] Other: **\*\***\_\_\_**\*\***

**Q1.3:** Will you have multiple authors/contributors?

- [x] No, just me (single author)
- [ ] Yes, 2-5 authors
- [ ] Yes, 5+ authors (need editorial workflow)
- [ ] Not sure yet

---

## 📝 SECTION 2: POSTS MANAGEMENT

### 2.1 Post Lifecycle & Status

**Q2.1:** Do you need all three statuses (draft/published/archived)?

- [ ] Yes, all three
- [x] Just draft/published (no archive)
- [ ] Other workflow: **\*\***\_\_\_**\*\***

**Q2.2:** Should archived posts be visible to public?

- [ ] No, archived = hidden from public
- [ ] Yes, archived posts should still be accessible via direct link
- [ ] Configurable per post
- [ ] Other: **\*\***\_\_\_**\*\***

**Q2.3:** Should there be a "scheduled publishing" feature?

- [x] Yes, I want to schedule posts for future publication (HIGH priority)
- [ ] Yes, but not urgent (MEDIUM priority)
- [ ] No, I'll publish manually
- [ ] Maybe in the future

**Q2.4:** Unpublish feature - what should happen?

- [ ] Move back to draft, clear published date
- [x] Keep published date, just hide from public
- [ ] Don't need unpublish, just archive
- [ ] Other: **\*\***\_\_\_**\*\***

---

### 2.2 Content & Rich Text

**Q2.5:** What content format will you use?

- [ ] Markdown (simple, no complex editor needed)
- [x] HTML/Rich Text (need WYSIWYG editor)
- [ ] Both (store as markdown, allow HTML too)
- [ ] Other: **\*\***\_\_\_**\*\***

**Q2.6:** Content field - do you need versioning/revision history?

- [ ] YES - I want to track all edits and restore old versions
- [ ] No, just keep latest version
- [x] Maybe in the future
- [ ] Not sure

**Q2.7:** Should there be a word count limit on posts?

- [x] No limit
- [ ] Yes, limit to **\_** words/characters
- [ ] Soft warning at **\_** words (but allow more)

---

### 2.3 Categories & Tags

**Q2.8:** Category behavior - one or many per post?

- [x] One category per post (as in PRD)
- [ ] Multiple categories per post
- [ ] Optional/no categories needed
- [ ] Other: **\*\***\_\_\_**\*\***

**Q2.9:** Should categories have hierarchy (parent/child)?

- [x] Yes, I want nested categories (e.g., Tech > JavaScript > React)
- [ ] No, flat categories are fine
- [ ] Not sure / decide later

**Q2.10:** Maximum tags per post?

- [ ] 10 (as in PRD)
- [ ] 5 (keep it simple)
- [ ] 20 (need more)
- [x] Unlimited
- [ ] Other: **\_**

**Q2.11:** Should you be able to create tags/categories inline when creating a post?

- [x] Yes, create on-the-fly if it doesn't exist
- [ ] No, must be created separately first (better control)
- [ ] Both options available

**Q2.12:** Should unused tags/categories be auto-cleaned?

- [ ] Yes, delete tags with 0 posts
- [x] No, keep all (I might reuse them)
- [ ] Manual cleanup only

---

### 2.4 Slugs & SEO

**Q2.13:** Slug generation - when should slugs be regenerated?

- [ ] Only on creation, never auto-update (stable URLs)
- [ ] Only when explicitly requested via `?regenerateSlug=true`
- [x] Auto-update whenever title changes
- [ ] Other: **\*\***\_\_\_**\*\***

**Q2.14:** Slug conflict resolution - what should happen?

- [ ] Auto-append -2, -3, etc. (as in PRD)
- [ ] Show error, let me manually fix it
- [x] Append timestamp/random string
- [ ] Other: **\*\***\_\_\_**\*\***

**Q2.15:** Custom slugs - should authors be able to set custom slugs?

- [x] Yes, allow manual slug editing
- [ ] No, always auto-generate from title
- [ ] Admin only can edit slugs

**Q2.16:** Meta description field:

- [ ] Required (enforce on publish)
- [ ] Optional but recommended
- [ ] Optional (no validation)
- [x] Auto-generate from content if empty

**Q2.17:** Do you need Open Graph (OG) tags support?

- [x] Yes - add fields: og_image, og_title, og_description
- [ ] No, use cover image + title + meta description
- [ ] Not needed

---

### 2.5 Cover Images

**Q2.18:** Cover image requirement:

- [x] Required for all posts
- [ ] Optional
- [ ] Required only for featured posts
- [ ] Other: **\*\***\_\_\_**\*\***

**Q2.19:** Should the system support multiple images per post (gallery)?

- [ ] Yes, I want image galleries
- [x] No, just one cover image
- [ ] Maybe in the future

**Q2.20:** Image optimization - should the API handle resizing/compression?

- [ ] Yes, auto-generate thumbnails (small/medium/large)
- [ ] No, I'll handle that in upload service
- [x] Not needed

---

### 2.6 Featured Posts

**Q2.21:** Featured posts - what does "featured" mean for you?

- [ ] Homepage spotlight (show on top)
- [ ] Different styling/prominence
- [ ] Both
- [x] Not sure yet

**Q2.22:** How many featured posts at once?

- [ ] 1 (only one featured at a time)
- [ ] 3-5 (featured section)
- [ ] Unlimited
- [x] Other: **\_**

---

### 2.7 Search & Filtering

**Q2.23:** Search scope - what should be searchable?

- [x] Title only (as in PRD)
- [ ] Title + content (full-text search)
- [ ] Title + content + tags + category
- [ ] Other: **\*\***\_\_\_**\*\***

**Q2.24:** Search technology:

- [x] Simple ILIKE (good enough for MVP)
- [ ] Postgres full-text search (to_tsvector)
- [ ] External service (Algolia, Elasticsearch, etc.)
- [ ] Not sure / start simple

**Q2.25:** Sort options - which do you need?

- [ ] Published date (newest first) - DEFAULT
- [ ] Published date (oldest first)
- [x] Most liked/popular
- [ ] Alphabetical (title)
- [ ] Random
- [ ] Other: **\*\***\_\_\_**\*\***

**Q2.26:** Pagination style:

- [ ] Offset-based (page=1, page=2, etc.) - as in PRD
- [x] Cursor-based (better for large datasets)
- [ ] Infinite scroll (load more)
- [ ] Not sure / start with offset

**Q2.27:** Default page size for public feed?

- [ ] 10 posts per page
- [x] 15 posts per page
- [ ] 20 posts per page
- [ ] Other: **\_**

---

## 💬 SECTION 3: COMMENTS

### 3.1 Comment System Basics -> Not need yet

**Q3.1:** Do you want a comment system?

- [ ] YES - high priority for MVP
- [ ] YES - but can be Phase 2
- [ ] NO - use external service (Disqus, etc.)
- [ ] Not sure yet

**Q3.2:** Comment authentication:

- [ ] Require login to comment
- [ ] Allow anonymous/guest comments (with name/email)
- [ ] Both (configurable)
- [ ] Other: **\*\***\_\_\_**\*\***

**Q3.3:** Comment moderation:

- [ ] Auto-approve all comments (trust users)
- [ ] Require admin approval before visible
- [ ] Auto-approve for registered users, moderate guests
- [ ] Other: **\*\***\_\_\_**\*\***

---

### 3.2 Threading & Replies -> Not need yet

**Q3.4:** Comment threading depth:

- [ ] Flat (no replies, all top-level)
- [ ] 1 level (comment + reply only)
- [ ] 2 levels (comment > reply > reply)
- [ ] Unlimited depth
- [ ] Other: **\_**

**Q3.5:** Should there be a "reply" notification?

- [ ] Yes, notify user when someone replies to their comment
- [ ] No, users can check manually
- [ ] Future feature

---

### 3.3 Comment Editing & Deletion -> Not need yet

**Q3.6:** Can users edit their own comments?

- [ ] Yes, anytime
- [ ] Yes, within 5-15 minutes of posting
- [ ] No, only admins can edit
- [ ] Other: **\*\***\_\_\_**\*\***

**Q3.7:** Comment deletion behavior:

- [ ] Soft delete (mark as "deleted", keep in DB)
- [ ] Hard delete (remove from DB completely)
- [ ] Show "[deleted]" placeholder if has replies
- [ ] Other: **\*\***\_\_\_**\*\***

**Q3.8:** Should deleted comments show "[deleted]" or disappear?

- [ ] Show "[deleted]" placeholder
- [ ] Remove completely
- [ ] Depends on if it has replies

---

### 3.4 Comment Visibility & Spam -> Not need yet

**Q3.9:** Should there be comment status (visible/hidden/deleted)?

- [ ] Yes (as in PRD)
- [ ] Just visible/deleted
- [ ] No status needed

**Q3.10:** Spam/abuse protection:

- [ ] Rate limiting (max X comments per minute)
- [ ] Content filtering (blacklist words)
- [ ] reCAPTCHA or similar
- [ ] Manual moderation only
- [ ] Other: **\*\***\_\_\_**\*\***

**Q3.11:** Rate limiting for comments:

- [ ] Max 5 comments per 10 minutes per user
- [ ] Max 10 comments per 10 minutes per user
- [ ] No rate limiting needed
- [ ] Other: **\_**

---

## 👍 SECTION 4: INTERACTIONS (Likes & Bookmarks)

### 4.1 Likes System

**Q4.1:** Do you want likes on posts?

- [x] YES - high priority
- [ ] YES - low priority
- [ ] NO - not needed
- [ ] Other: **\*\***\_\_\_**\*\***

**Q4.2:** Do you want likes on comments?

- [ ] YES - high priority
- [ ] YES - low priority
- [x] NO - just posts
- [ ] Other: **\*\***\_\_\_**\*\***

**Q4.3:** Like visibility:

- [x] Show like count to everyone
- [ ] Show like count only to logged-in users
- [ ] Show list of who liked (public)
- [ ] Show list of who liked (only to author)
- [ ] Hide counts completely (just toggle)

**Q4.4:** Unlike behavior:

- [ ] Allow users to unlike anytime
- [ ] Cannot unlike once liked
- [ ] Other: **\*\***\_\_\_**\*\***

---

### 4.2 Bookmarks

**Q4.5:** Do you want bookmarks (save for later)?

- [x] YES - high priority
- [ ] YES - low priority
- [ ] NO - not needed
- [ ] Other: **\*\***\_\_\_**\*\***

**Q4.6:** Bookmark privacy:

- [x] Private (only user sees their bookmarks)
- [ ] Public (show who bookmarked on post)
- [ ] Optional (user chooses)
- [ ] Other: **\*\***\_\_\_**\*\***

**Q4.7:** Should bookmarks have categories/folders?

- [ ] Yes, let users organize bookmarks into folders
- [x] No, just a flat list
- [ ] Future feature

---

### 4.3 Counters & Performance

**Q4.8:** Like/bookmark counters - how should they be stored?

- [ ] Real-time COUNT(\*) queries (simple, accurate)
- [ ] Denormalized counter columns (faster, needs transaction)
- [ ] Cached counts (fast, eventual consistency)
- [x] Not sure / start simple

**Q4.9:** Should like counts affect search/sort?

- [x] Yes, add "popular" sort by like count
- [ ] No, just show counts
- [ ] Future feature

---

### 4.4 Rate Limiting

**Q4.10:** Rate limiting for likes/bookmarks:

- [ ] Yes, max 10 toggles per 10 seconds (as in PRD)
- [ ] Yes, but more lenient (max 20 per 10 seconds)
- [x] No rate limiting needed
- [ ] Other: **\_**

---

## 🔐 SECTION 5: AUTHORIZATION & ROLES

### 5.1 User Roles

**Q5.1:** What user roles do you need?

- [x] Just "user" and "admin" (simple)
- [ ] user, author, editor, admin (editorial workflow)
- [ ] user, author, admin (as in PRD)
- [ ] Other: **\*\***\_\_\_**\*\***

**Q5.2:** Can regular users create posts? -> Not need yet

- [ ] Yes, anyone can create drafts (need approval)
- [ ] No, only author/admin can create posts
- [ ] Configurable

**Q5.3:** Multi-author setup - author permissions: -> Not need yet

- [ ] Authors can only CRUD their own posts
- [ ] Authors can view all posts but edit only theirs
- [ ] Editors can edit any post
- [ ] Other: **\*\***\_\_\_**\*\***

---

### 5.2 Post Visibility & Access -> Not need yet

**Q5.4:** Draft post access:

- [ ] Only author + admin can view/edit
- [ ] Share draft via secret link (preview mode)
- [ ] Only author
- [ ] Other: **\*\***\_\_\_**\*\***

**Q5.5:** Archived post access:

- [ ] Author + admin only
- [ ] Anyone with direct link
- [ ] Completely hidden
- [ ] Other: **\*\***\_\_\_**\*\***

---

## 📊 SECTION 6: ANALYTICS & TRACKING

### 6.1 View Counts

**Q6.1:** Do you want post view tracking?

- [x] Yes, track views in database
- [ ] Yes, but use external service (Google Analytics, Plausible, etc.)
- [ ] No, not needed
- [ ] Future feature

**Q6.2:** If yes, what counts as a "view"?

- [ ] Every page load
- [x] One per session
- [ ] One per user per day
- [ ] Other: **\*\***\_\_\_**\*\***

---

### 6.2 Activity Logging

**Q6.3:** Should the API log user activities (audit trail)?

- [ ] Yes, log all create/update/delete actions
- [ ] Only log sensitive actions (publish, delete)
- [x] No, not needed
- [ ] Not sure

---

## 🔔 SECTION 7: NOTIFICATIONS (Future) -> Not need yet

**Q7.1:** Will you need notifications in the future?

- [ ] Yes, email notifications (new comment, reply, like)
- [ ] Yes, in-app notifications
- [ ] Both
- [ ] No, not needed
- [ ] Not sure yet

**Q7.2:** If yes, what events should trigger notifications?

- [ ] Comment on my post
- [ ] Reply to my comment
- [ ] Someone liked my post/comment
- [ ] New follower (if you add social features)
- [ ] Other: **\*\***\_\_\_**\*\***

---

## 🚀 SECTION 8: PERFORMANCE & OPTIMIZATION

### 8.1 Caching

**Q8.1:** Do you want API-level caching?

- [ ] Yes, cache public feeds/post details (5-15 min TTL)
- [ ] No, keep it simple
- [x] Future optimization
- [ ] Not sure

**Q8.2:** If yes, preferred caching solution:

- [x] Redis
- [ ] In-memory (node-cache)
- [ ] CDN-level caching
- [ ] Not sure / recommend one

---

### 8.2 Database Optimization

**Q8.3:** Are you comfortable with:

- [x] Denormalized counters (faster reads, more complex writes)
- [ ] Real-time queries (simpler, might be slower at scale)
- [ ] Hybrid approach (start simple, optimize later)
- [ ] Not sure / need guidance

---

## 🧪 SECTION 9: TESTING & QUALITY

**Q9.1:** Testing requirements:

- [ ] Unit tests for all services (high coverage)
- [ ] Integration tests for main flows
- [x] E2E API tests only
- [ ] Manual testing is fine for MVP
- [ ] Other: **\*\***\_\_\_**\*\***

**Q9.2:** API documentation preference:

- [ ] OpenAPI/Swagger (auto-generated docs)
- [ ] Postman/Insomnia collection
- [ ] Markdown documentation
- [ ] All of the above
- [x] Not needed

---

## 📦 SECTION 10: DATA & SEEDING

**Q10.1:** Do you want seed data for development?

- [ ] Yes, generate realistic fake data (10+ posts, comments, etc.)
- [x] Yes, just a few samples (3-5 posts)
- [ ] No, I'll create my own content
- [ ] Not sure

**Q10.2:** Import/export features:

- [ ] Need to import posts from another platform (WordPress, Medium, etc.)
- [ ] Need export to JSON/backup
- [ ] Both
- [x] Not needed now
- [ ] Future feature

---

## 🎯 SECTION 11: PRIORITIES & TIMELINE

**Q11.1:** Feature priority ranking (1 = highest, 5 = lowest):

- [ ] Posts CRUD & publishing workflow: **\_**
- [ ] Categories & Tags: **\_**
- [ ] Search & Filtering: **\_**
- [ ] Comments system: **\_**
- [ ] Likes & Bookmarks: **\_**
- [ ] SEO features (slugs, meta): **\_**
- [ ] Scheduled publishing: **\_**

**Q11.2:** What's your MVP definition (minimum for launch)?

- [ ] Just posts + categories + basic auth
- [ ] Posts + categories + tags + search
- [x] Everything except comments
- [ ] Everything in the PRD as-is
- [ ] Other: **\*\***\_\_\_**\*\***

**Q11.3:** Timeline expectation:

- [x] Need MVP in 1-2 weeks
- [ ] Can take 1 month for full features
- [ ] No rush, quality over speed
- [ ] Other: **\*\***\_\_\_**\*\***

---

## 💡 SECTION 12: ADDITIONAL FEATURES & IDEAS

**Q12.1:** Any features NOT in the PRD you want to add?
Commentes, like

---

---

---

**Q12.2:** Any features in the PRD you want to REMOVE or simplify?
Commentes, like

---

---

---

**Q12.3:** Other concerns or requirements?
view number using for tracking popular post

---

---

---

---

## 🎨 SECTION 13: CODE PREFERENCES

**Q13.1:** Error handling preference:

- [x] Keep the new centralized error handling (as we just implemented)
- [ ] Go back to try-catch in controllers
- [ ] Other approach: **\*\***\_\_\_**\*\***

**Q13.2:** Response format preference:

- [x] Current format: `{ success, status, message, data }`
- [ ] Simpler: `{ data, meta }`
- [ ] Custom format: **\*\***\_\_\_**\*\***

**Q13.3:** Code organization preference:

- [x] Keep current structure (controllers → services → repositories)
- [ ] Simpler (controllers → DB directly)
- [ ] Add more layers (use cases, etc.)
- [ ] Not sure / trust your judgment

---

## ✅ COMPLETION

**Thank you for filling out this survey!**

Please save this file and share it with me. I'll use your answers to:

1. Generate a new, detailed PRD that matches your exact needs
2. Create a prioritized implementation plan
3. Build a better, cleaner backend architecture

**Questions or need clarification on any question?** Let me know!

---

**Survey completed on:** **\*\***\_\_\_**\*\***  
**Any immediate concerns:** **\*\***\_\_\_**\*\***
