# CampusChronicle

A full-stack blogging platform where writers publish rich, media-friendly posts and readers engage through likes, nested comments and real-time notifications. Originally built for students at Government Engineering College, Rajkot, so seniors could share their experience with juniors.

**Live demo:** https://gecr-blogs.netlify.app · **Backend:** [CampusChronicle-Server](https://github.com/Ritu84/CampusChronicle-Server)

![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=flat-square&logo=tailwind-css&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=flat-square&logo=express&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase_Auth-FFCA28?style=flat-square&logo=firebase&logoColor=black)
![AWS S3](https://img.shields.io/badge/AWS_S3-569A31?style=flat-square&logo=amazons3&logoColor=white)

## Features

**Writing**
- Block-based rich text editor (Editor.js) with headings, lists, quotes, code, links, embeds and inline images
- Image uploads straight to **AWS S3** through pre-signed upload URLs
- Save drafts, publish with tags and a short description, edit or delete later

**Reading & discovery**
- Home feed of latest posts with pagination, plus a **trending** section and tag filters
- Search across blogs and users
- Unique, shareable URL for every post

**Engagement**
- Likes and **nested comments** with replies and deletion
- **Notifications** for likes, comments and replies, with new ones highlighted

**Accounts**
- Email/password sign-up (bcrypt-hashed) and **Google sign-in** via Firebase
- JWT-protected API routes
- Public profiles with bio, social links and written posts; edit profile, profile photo and password

**Dashboard**
- Manage published posts and drafts in one place, with per-post stats (likes, comments, reads)
- Responsive design, light/dark theme and page-transition animations (Framer Motion)

## Architecture

```
React (Vite) client  ──►  Express REST API  ──►  MongoDB (Mongoose)
       │                        │
       └── Firebase (Google sign-in)   └── AWS S3 (image storage via signed URLs)
```

Main data models: **User**, **Blog**, **Comment** (with parent/child replies) and **Notification**.

## Running Locally

**Backend** (in [CampusChronicle-Server](https://github.com/Ritu84/CampusChronicle-Server) or the `server/` folder):
```bash
cd server
npm install
npm start
```
Create `server/.env`:
```
DB_LOCATION=your_mongodb_connection_string
SECRET_ACCESS_KEY=your_jwt_secret
AWS_ACCESS_KEY=your_aws_access_key
AWS_SECRET_ACCESS_KEY=your_aws_secret_key
```
You also need a Firebase service account file for Google sign-in.

**Frontend**:
```bash
cd frontend
npm install
npm run dev
```
Create `frontend/.env`:
```
VITE_SERVER_DOMAIN=http://localhost:3000
```

## Project Structure

```
CampusChronicle/
├── frontend/
│   └── src/
│       ├── pages/        # Home, blog, editor, search, profile, dashboard, notifications, settings
│       ├── components/   # Editor, blog cards, comments, navigation, notification cards
│       └── common/       # Session, Firebase, S3 upload, date and pagination helpers
└── server/
    ├── Schema/           # User, Blog, Comment, Notification models
    └── server.js         # REST API
```

## Author

**Ritu Sharma** · [GitHub](https://github.com/Ritu84) · [LinkedIn](https://www.linkedin.com/in/ritu-sharma-a2580222a/)
