🌐 Hybrid File System with Cloud Backup and Metadata Tracking
This project implements a hybrid virtual file system that supports basic file and directory operations, persistent metadata storage using SQLite, and cloud backup/restore using Google Drive API.

🚀 Features
1. ✅ Create/Delete Files and Directories
2. 📝 Read, Write, and Append File Content
3. 💾 Persistent Metadata Storage in SQLite (with timestamping)
4. ☁️ Automatic Google Drive Backup (Upload/Download/Restore)
5. 🔄 Folder Synchronization between Local and Cloud
6. 📊 Metadata Inspection via CLI (checkmetadata.py)

📁 Project Structure
├── main3.py               # CLI for interacting with the file system
├── init.py                # Initializes the SQLite metadata DB
├── checkmetadata.py       # CLI to view file metadata
├── filesystem.json        # Local representation of the virtual file system
├── metadata/
│   ├── db.py              # Database operations
│   ├── schema.sql         # Schema + trigger for metadata tracking
├── cloud/
│   ├── g_drive.py          # Google Drive API integration
│   ├── credentials.json   # OAuth credentials (not included)
│   ├── token.json         # OAuth token (auto-generated)

🛠️ Setup Instructions
1. Install Required Packages
   pip install -r requirements.txt
2. Setup Google Drive API
   Go to Google Cloud Console
   Enable Google Drive API
   Create OAuth 2.0 Client ID
   Download credentials.json and place it in the cloud/ folder

🧑‍💻 How to Use
1. Initialize Database
   python init.py
2. Run the File System CLI
   python main3.py
3. Available Commands
   | Command                         | Description                                                     
 ------------------------------- | ----------------------------  
 `mkdir /dir`                    | Create a new directory                                             
 `create /dir/file.txt`          | Create a file                                                      
 `write /dir/file.txt "Hello"`   | Overwrite file content                                             
 `append /dir/file.txt " World"` | Append to file                                                     
 `read /dir/file.txt`            | Display file content                                               
 `ls /dir`                       | List directory contents                                            
 `delete /dir/file.txt`          | Delete file or directory                                           
 `download file.txt`             | Download file from Drive                                           
 `deletecloud file.txt`          | Delete file from Drive                                             
 `restoreall`                    | Restore all Drive files                                            
 `syncfolder /dir`               | Sync local folder with Drive                                       
 `exit`                          | Exit the CLI                 
4. View Metadata
   python checkmetadata.py

🧠 Technical Concepts Used
1. Python Dictionaries for in-memory virtual FS
2. SQLite for persistent metadata storage
3. Google Drive API (OAuth 2.0 + REST calls)
4. File system synchronization logic
5. Timestamps managed via SQLite triggers

⚠️ Notes
1. The credentials.json and token.json are required for Drive operations and should not be shared publicly.
2. Cloud deletion (deletecloud) is a manual command for safety.
3. Google Drive API has quota limits. Use responsibly.
   
