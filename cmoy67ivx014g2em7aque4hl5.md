---
title: "Storing Uploaded Files and Serving Them in Express"
seoTitle: "Storing Uploaded Files and Serving Them in Express"
seoDescription: "Storing Uploaded Files and Serving Them in Express"
datePublished: 2026-05-09T09:57:44.928Z
cuid: cmoy67ivx014g2em7aque4hl5
slug: storing-uploaded-files-and-serving
tags: javascript, multer, file-handling, chaicode

---

File uploads are everywhere in backend applications.

Examples:

*   profile pictures
    
*   PDFs
    
*   videos
    
*   resumes
    
*   product images
    

But many only focus on the upload part and forget an important question:

> “Where do these files actually go after upload?”

And another one:

> “How are they later accessible from the browser?”

To understand file uploads properly in Express, we need to understand:

*   storage
    
*   static file serving
    
*   public URLs
    
*   safe handling practices
    

* * *

# What Happens During File Upload?

When a user uploads a file:

1.  browser sends file data to server
    
2.  Express receives the request
    
3.  server stores the file somewhere
    
4.  server later serves that file when requested
    

The important part is: uploaded files do not magically become accessible.

You must explicitly:

*   store them
    
*   expose them
    
*   serve them
    

* * *

# Where Uploaded Files Are Stored

In many Express applications, uploaded files are stored inside a folder like:

```txt
project/
├── uploads/
│   ├── image1.png
│   ├── resume.pdf
│   └── avatar.jpg
├── server.js
```

This folder acts as local file storage.

* * *

# Why Local Storage Exists

The server needs a physical location to save incoming files.

Without storage:

*   uploaded files disappear after request completion
    
*   users cannot access them later
    

Local storage is the simplest approach because files are stored directly on the server machine.

* * *

# Example Upload Handling

Libraries like `multer` are commonly used.

Example:

```js
const multer = require("multer");

const upload = multer({
  dest: "uploads/"
});
```

This tells Express:

> “Store uploaded files inside the uploads folder.”

* * *

# Local Storage vs External Storage

There are two major storage approaches.

* * *

# 1\. Local Storage

Files stored directly on server disk.

Example:

```txt
uploads/
```

## Advantages

*   simple setup
    
*   fast for small projects
    
*   easy development workflow
    

## Problems

*   server disk can fill up
    
*   scaling becomes difficult
    
*   files may disappear during deployments
    
*   multiple servers cannot easily share files
    

* * *

# 2\. External Storage

Files stored in dedicated storage services.

Examples:

*   AWS S3
    
*   Cloudinary
    
*   Google Cloud Storage
    

Instead of saving files locally:

*   server uploads files to external provider
    
*   provider manages storage and delivery
    

* * *

# Why External Storage Exists

Large-scale applications may handle:

*   millions of images
    
*   videos
    
*   large documents
    

Keeping everything on one server becomes unreliable.

External storage solves:

*   scalability
    
*   backups
    
*   CDN delivery
    
*   distributed access
    

* * *

# Serving Static Files in Express

Uploading files is only half the system.

Users also need access to those files.

By default, Express does not expose folders publicly.

If an image exists inside:

```txt
uploads/avatar.png
```

the browser cannot access it automatically.

You must explicitly serve it.

* * *

# Static File Serving

Express provides:

```js
express.static()
```

Example:

```js
app.use("/uploads", express.static("uploads"));
```

This creates a public route.

Now:

```txt
uploads/avatar.png
```

becomes accessible through:

```txt
http://localhost:3000/uploads/avatar.png
```

* * *

# What Actually Happens?

Flow:

```txt
Browser requests image URL
↓
Express checks static folder
↓
Matching file found
↓
File returned as response
```

Express acts like a file server.

* * *

# Why Static Serving Exists

Browsers need URLs, not file system paths.

The browser cannot access:

```txt
/home/project/uploads/avatar.png
```

But it can access:

```txt
https://example.com/uploads/avatar.png
```

Static serving maps server folders to public URLs.

* * *

# Example Real-World Upload Flow

```txt
User uploads image
↓
Express receives file
↓
File stored in uploads folder
↓
Database stores file path
↓
Frontend receives image URL
↓
Browser requests image later
↓
Express serves static file
```

This is how profile pictures and uploaded content usually work.

* * *

# Important Security Considerations

File uploads are dangerous if handled carelessly.

Because users can upload:

*   malicious files
    
*   huge files
    
*   executable scripts
    
*   fake file types
    

Safe handling is extremely important.

* * *

# 1\. Validate File Types

Never trust file extensions alone.

Example bad upload:

```txt
virus.exe renamed to image.png
```

Always validate MIME types and allowed formats.

* * *

# 2\. Limit File Size

Without limits:

*   attackers can upload huge files
    
*   server storage may crash
    

Example:

```js
limits: {
  fileSize: 5 * 1024 * 1024
}
```

This limits uploads to 5MB.

* * *

# 3\. Rename Uploaded Files

Never trust original filenames directly.

Bad:

```txt
../../../system-file
```

Many systems generate unique filenames automatically to avoid:

*   collisions
    
*   path traversal issues
    
*   malicious naming
    

* * *

# 4\. Avoid Public Access to Everything

Not every uploaded file should be publicly accessible.

Examples:

*   private documents
    
*   invoices
    
*   user reports
    

Some files should require authentication before serving.

* * *

# 5\. Separate Uploads From Application Code

Good structure:

```txt
project/
├── src/
├── uploads/
├── public/
```

This avoids accidental execution or exposure of sensitive files.

* * *

# Simple Mental Model

Think of uploaded files like this:

## Uploading

> “Store the file somewhere safely.”

* * *

## Static Serving

> “Create a public URL for accessing it.”

* * *

## Security

> “Never trust uploaded data blindly.”

* * *

File uploads in Express are more than just accepting files from users.

A complete upload system involves:

*   storage strategy
    
*   static serving
    
*   public access management
    
*   validation
    
*   security controls
    

For small applications, local storage is often enough.

For scalable production systems, external storage solutions are usually preferred.

The key realization is:

Uploading files and serving files are two separate responsibilities.

One stores data. The other exposes it safely to users.