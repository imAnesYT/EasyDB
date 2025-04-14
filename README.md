<h1 align="center">EasyDB</h1>

<p align="center">
  A simple, beginner-friendly SQLite3-based key-value store for Python applications.
</p>

<p align="center">
  <a href="https://pypi.org/project/easy-db3/"><img src="https://badge.fury.io/py/easy-db3.svg" alt="PyPI version"></a>
  <a href="https://github.com/imAnesYT/easydb/blob/main/LICENSE"><img src="https://img.shields.io/github/license/imAnehsYT/easydb" alt="License"></a>
  <a href="https://pepy.tech/project/easy-db3"><img src="https://pepy.tech/badge/easy-db3" alt="Downloads"></a>
  <a href="https://www.python.org/"><img src="https://img.shields.io/badge/python-3.6%2B-blue.svg" alt="Python"></a>
</p>

---

## 📦 Installation

Install EasyDB from PyPI:

```bash
pip install easy-db3
```

## 🔧 Usage
```python
import easydb
from easydb import Database

# Create an instance of the Database class
db = Database("example.db")

# --- Step 1: Store Data ---
# Store some user data under the "USER" category
db.storage("name: Alice", "age: 28", category="USER")
db.storage("admin: True", category="USER")

# Store server and channel data under "CHANNELS" category
db.storage("server_id: 9876", "channel_id: 1234", category="CHANNELS")

# --- Step 2: Load Data ---
db.load()

# --- Step 3: Retrieve Data ---
print("User Name:", db.get_data("name", category="USER"))  # Alice
print("User Age:", db.get_data("age", category="USER"))    # 28
print("Admin:", db.get_data("admin", category="USER"))     # True
print("User Category Data:", db.get_data(category="USER"))
# Output: {'name': 'Alice', 'age': '28', 'admin': 'True'}

print("Server ID:", db.get_data("server_id", category="CHANNELS"))      # 9876
print("Channel ID:", db.get_data("channel_id", category="CHANNELS"))    # 1234
print("Channels Category Data:", db.get_data(category="CHANNELS"))
# Output: {'server_id': '9876', 'channel_id': '1234'}

# --- Step 4: Delete Data ---
db.del_data("age", category="USER")
print("After Deleting Age from USER:", db.get_data(category="USER"))
# Output: {'name': 'Alice', 'admin': 'True'}

db.del_data(category="USER")
print("After Deleting USER category:", db.get_data(category="USER"))
# Output: None

# --- Step 5: Flat Structure ---
db.storage("app_name: MyApp")
db.load()
print("App Name:", db.get_data("app_name"))  # MyApp
db.del_data("app_name")
print("After Deleting app_name:", db.get_data("app_name"))  # None

# --- Step 6: Save Changes ---
# All changes are saved automatically after storage or deletion.
# You can manually save using db._save() if needed.
```
