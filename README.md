
# Elixir Launcher Setup 
---

### **Features**
1. **Download PAK Files**  
   - Download files from a specified URL to a local path.  
   - Tracks download progress and emits updates for UI feedback.  

2. **File Management**  
   - Check if a file exists locally before downloading.  
   - Verify file sizes.  

3. **Progress Tracking**  
   - Real-time updates using Tauri's `emit_all` system.  
   - Provides detailed progress, including transfer rates and percentages.  

4. **Error Handling**  
   - Captures and logs errors during file downloads.  
   - Ensures safe file operations.

---

### **Setup**
1. **Dependencies**  
   The following Rust crates are used:
   - `tauri`: Provides command and event systems.
   - `reqwest`: Handles HTTP requests for downloading files.
   - `serde`: Serializes and deserializes progress data.
   - `indicatif`: Displays a progress bar in the terminal.

2. **Commands**
   - `download_paks`: Downloads a file from a base URL.  
   - `check_pak_exists`: Checks for a specific PAK file in a given directory.  
   - `get_file_size`: Retrieves the size of a file.  
   - `check_file_exists`: Verifies if a file exists.

3. **Tauri Events**
   - `DOWNLOAD_PROGRESS_PAK`: Sent periodically with progress updates.  
   - `DOWNLOAD_FINISHED_PAK`: Sent when a download completes.

---

### **Usage**
1. **Download a File**
   Call the `download_paks` command with:  
   - `base_url`: URL of the server hosting PAK files.  
   - `file_name`: Name of the file to download.  
   - `path`: Destination directory on the local machine.

   Example:
   ```rust
   download_paks("https://example.com", "example.pak", "/local/path", app_handle).await;
   ```

2. **Check if a File Exists**
   ```rust
   let exists = check_pak_exists("/local/path", "example.pak").await?;
   ```

3. **Get File Size**
   ```rust
   let size = get_file_size("/local/path/example.pak").await?;
   ```

---

### **Progress Example**
- Emits progress updates:
  ```json
  {
    "download_id": 1,
    "filesize": 102400,
    "transfered": 51200,
    "transfer_rate": 2048.0,
    "percentage": 50.0,
    "comment": "Halfway done"
  }
  ```
- Emit upon completion:
  ```json
  {
    "download_id": 1,
    "filesize": 102400,
    "transfered": 102400,
    "percentage": 100.0,
    "comment": "Download finished"
  }
  ```

---

### **How to Contribute**
1. **Clone the Repository**
   ```bash
   git clone https://github.com/your-repo/tauri-pak-downloader.git
   cd tauri-pak-downloader
   ```
2. **Install Dependencies**
   Ensure you have Rust and Tauri installed:
   ```bash
   cargo install tauri-cli
   ```
3. **Run the Application**
   Use `cargo` to build and run:
   ```bash
   cargo run
   ```
---
# Debug App

- 1 cd "PASTE UR SRC PATH"
- 2 yarn install
- 3 yarn tauri dev



