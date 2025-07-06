# 📄 Changelog

## [0.4.0] – 2025-06-20

🎉 **First public release of Fold Test Node.js GitHub Action**

### ✨ Added
- Starts a Fold Server instance from a local mock project or single file
- Supports running custom test and frontend commands in CI
- Configurable ports, working directory, and CORS origins

### 📦 Action Inputs

| Input       | Required | Description                                                  |
|-------------|----------|--------------------------------------------------------------|
| `test`      | ✅       | Command to run tests (e.g. `npm run test`)                   |
| `dir`       | ✅       | Path to mock project directory or file                       |
| `work_dir`  | ❌       | Directory where test command will run                        |
| `run`       | ❌       | Command to run frontend (executed before test)               |
| `port`      | ❌       | Port override (if default not used)                          |
| `origin`    | ❌       | CORS origin setting for frontend/backend separation          |
| `file`      | ❌       | Serve a single file instead of a directory                   |

### Check this example repository
https://github.com/ognerezov/fold-next-test-example

### See full documentation for fold server tool
https://github.com/ognerezov/fold

---

📚 Full docs available in the [README](https://github.com/ognerezov/fold-test-node)  
🐛 Found an issue? [Open an issue](https://github.com/ognerezov/fold-test-node/issues)  
📩 Questions? Contact [ognerezov@foldserver.net](mailto:ognerezov@foldserver.net)
