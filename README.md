# Fold Test Node.js Action

A GitHub Action for running tests with a mock server for Node.js projects.

## Features
- Starts a Fold test server alongside your tests.
- Configurable test command and working directory.
- Supports custom ports and CORS origins.

## Inputs

| Input       | Required | Default       | Description                                    |
|-------------|----------|---------------|------------------------------------------------|
| `test`      | Yes      | `npm run test`| Shell command to run tests.                    |
| `dir`       | Yes      | `/fold`       | Path to Fold server project files.             |
| `work_dir`  | No       | (current dir) | Path to source code where tests run.           |
| `run`       | No       | -             | Shell command to start frontend app.           |
| `port`      | No       | -             | Backend port (if not set in folder structure). |
| `origin`    | No       | -             | Allowed CORS origins (if FE ≠ port 3000).      |
| `file`      | No       | -             | Serve single file instead of folder.           |

## Usage

### Basic Example
```yaml
steps:
  - uses: actions/checkout@v4
  - uses: ognerezov/fold-test-node@main
    with:
      dir: '/path/to/fold'
      test: 'npm test'
```

### Full Example (with installation)
```yaml
jobs:
  integration_tests:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: ognerezov/fold-test-node@main
        with:
          dir: '/github/workspace/mock'
          work_dir: '/github/workspace'
          test: 'npm install && npm run test'
          port: 8080
          origin: 'http://localhost:3001'
```

### Frontend+Backend Testing
```yaml
steps:
  - uses: ognerezov/fold-test-node@main
    with:
      dir: './mock-server'
      work_dir: './app'
      run: 'npm start'       # Frontend command
      test: 'npm run test'   # Test command
      origin: 'http://localhost:3001'
```

## How It Works
1. Starts the Fold server using your specified `dir`.
2. Runs your `test` command in `work_dir`.
3. (Optional) Runs frontend via `run` if provided.
4. Returns test results with server logs.

---

### Notes:
- For private repos, ensure `actions/checkout@v4` has access.
- Use `port` only if Fold doesn't auto-detect ports.
- Set `origin` if your frontend runs on non-3000 ports.

### Check this example repository
https://github.com/ognerezov/fold-next-test-example

### See full documentation for fold server tool
https://github.com/ognerezov/fold