# this is a project to learn and apply backend

### Multer

```txt
What is Multer?

    => Multer = middleware for handling file uploads in Express

    Normal express.json() -> cannot handle files
    Multer -> handles multipart/form-data
    Ex: form-data (images, videos, files)

```

## Multer Big Picture

```txt

    Multer = delivery boy
    destination = where to deliver
    filename = what name to write
    cb = instruction you give to delivery boy

```

## Steps for using multer

```txt
1. Import multer (Bringing multer into your project)
    import multer from "multer";

2. Storage Configuration
    const storage = multer.diskStorage({})

=> You are telling multer : "Store uploaded files on disk (local system)"

3. destination
    destination: function (req, file, cb) {
        cb(null, "./public/temp")
    }

=> cb = callback
    cb(error, destination)
    cb(null, "./public/temp")

    => No error → save file in ./public/temp

4. filename
    filename: function (req, file, cb) {
        cb(null, file.originalname)
    }

    => Use same name as uploaded file

5. Create multer instance
    export const upload = multer({
        storage,
    })

    => This creates middleware you will use in routes

```

## Flow

```txt

Frontend sends form-data
    ↓
Multer middleware runs
    ↓
File saved to ./public/temp
    ↓
req.files populated
    ↓
Controller accesses file path
    ↓
Upload to Cloudinary
    ↓
Delete local file

```

# Questions

```txt

1: What is diskStorage?
Answer:

    A storage engine provided by multer to store files on local disk.

2: What is cb in multer?
Answer:

    A callback function used to pass result (destination/filename) or error to multer.

3: Why use cb(null, value)?
Answer:

    Because Node.js follows error-first callback pattern.

4: What is file object?
Answer:

    An object containing metadata of uploaded file.

5: Why use callback instead of return?
Answer:

    To support asynchronous control and follow Node.js conventions.

```
