# Node.js Git-based File Management API

## Overview

This Node.js application provides an API to update markdown files and upload files to a Git repository. It utilizes Express, Multer, Simple-Git, and other dependencies to manage file updates and commits within a specified Git repository.

## Features

- Clone a remote Git repository.
- Update a markdown file and commit changes.
- Upload a file to a specific path in the repository and commit changes.
- Automatically clean up cloned repositories after processing.

## Prerequisites

Ensure you have the following installed:

- Node.js (v14 or later recommended)
- Git

## Installation

1. Clone the repository:
   ```sh
   git clone <your-repo-url>
   cd <your-project-folder>
   ```
2. Install dependencies:
   ```sh
   npm install
   ```
3. Configure repository details in `index.js`:
   - Update `REPO_URL` with your repository URL.
   - Set `BRANCH_NAME` to the branch you want to work with.
   - **Note:** If you face issues with `REPO_URL`, you might need to add it directly in the remote add call on **line 99** in `index.js`.

## Usage

### Start the Server

Run the following command to start the server:

```sh
node index.js
```

The server will run on port `4000`.

### API Endpoints

#### 1. Test Server

- **Endpoint:** `GET /`
- **Response:** "This works!"

#### 2. Update Markdown File

- **Endpoint:** `POST /update-md`
- **Request Body:**
  ```json
  {
    "filePath": "path/to/your/file.md",
    "markdownContent": "# New Markdown Content"
  }
  ```
- **Functionality:**
  - Clones the Git repository.
  - Updates the specified markdown file.
  - Commits and pushes changes.
  - Cleans up the cloned repository.

#### 3. Upload a File

- **Endpoint:** `POST /upload-file`
- **Form Data:**
  - `file`: The file to be uploaded.
  - `repoPath`: The directory within the repo to place the file.
- **Functionality:**
  - Clones the repository if not already present.
  - Uploads the file to the specified directory.
  - Commits and pushes changes.
  - Cleans up the cloned repository.

You can use **Postman** to test this API. For file uploads, go to the "Body" section in Postman, select "form-data", and upload a file directly.

## Cleanup

To prevent storage issues, cloned repositories are removed after each request using `rimraf`.

## Dependencies

- `express` - Web framework for Node.js
- `cors` - Enable Cross-Origin Resource Sharing
- `body-parser` - Parse incoming JSON requests
- `multer` - Handle file uploads
- `simple-git` - Git commands in Node.js
- `fs` & `path` - File system operations
- `rimraf` - Remove directories recursively

## License

This project is licensed under the MIT License.
