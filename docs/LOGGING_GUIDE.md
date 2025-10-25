# Logging System Quick Reference

## 🎨 Log Levels and Colors

When you start the server, you'll see colored logs:

- 🟢 **[info]** - Green - General information (server start, successful operations)
- 🔵 **[http]** - Cyan - HTTP requests with timing
- 🟡 **[warn]** - Yellow - Warnings (4xx errors, validation issues)
- 🔴 **[error]** - Red - Errors (5xx errors, exceptions)
- 🔷 **[debug]** - Blue - Debug information (only in development)

## 📝 Usage Examples

### Import the logger
```javascript
import logger from "./config/logger.js";
```

### Basic logging
```javascript
// Information
logger.info("User registered successfully");

// HTTP requests (automatically logged by middleware)
// [http] 2025-10-21 21:39:45: POST /api/auth/register 201 - 89ms - ::1

// Warnings
logger.warn("Invalid file format uploaded");

// Errors
logger.error("Database connection failed", error);

// Debug (only shown if LOG_LEVEL=debug)
logger.debug("Processing order data:", orderData);
```

### In Controllers
```javascript
export const createUser = async (req, res, next) => {
  try {
    const user = await userService.create(req.body);
    
    logger.info(`User created: ${user.id}`);
    
    sendSuccess(res, user, "User created successfully");
  } catch (error) {
    logger.error("Failed to create user:", error);
    next(error);
  }
};
```

### With Metadata
```javascript
logger.info("Payment processed", {
  userId: "123",
  amount: 99.99,
  currency: "USD"
});

// Output: [info] 2025-10-21 21:39:45: Payment processed {"userId":"123","amount":99.99,"currency":"USD"}
```

## 📂 Log Files

All logs are automatically saved to `logs/` directory:

- `combined-YYYY-MM-DD.log` - All logs
- `error-YYYY-MM-DD.log` - Error logs only
- `exceptions-YYYY-MM-DD.log` - Unhandled exceptions
- `rejections-YYYY-MM-DD.log` - Unhandled promise rejections

Files rotate daily and are kept for 14 days.

## ⚙️ Configuration

Set log level in `.env`:

```env
LOG_LEVEL=info  # Options: error, warn, info, http, debug
```

**Production:** Use `LOG_LEVEL=warn` or `LOG_LEVEL=error`  
**Development:** Use `LOG_LEVEL=info` or `LOG_LEVEL=debug`

## 🚫 Don't Use console.log

❌ **Old way:**
```javascript
console.log("User logged in");
console.error("Error:", error);
```

✅ **New way:**
```javascript
import logger from "./config/logger.js";

logger.info("User logged in");
logger.error("Error:", error);
```

## 🔍 Viewing Logs

### Development (Console)
Just run `npm start` and watch the colored output in your terminal.

### Production (Files)
```bash
# View latest combined logs
cat logs/combined-2025-10-21.log

# View latest errors only
cat logs/error-2025-10-21.log

# Watch logs in real-time
tail -f logs/combined-2025-10-21.log

# Search for specific user
grep "user-id-123" logs/combined-*.log
```

## 📊 Request Logging

Every HTTP request is automatically logged with:
- Method (GET, POST, etc.)
- URL path
- Status code
- Response time in milliseconds
- Client IP

Example output:
```
[http] 2025-10-21 21:39:45: GET /api/users 200 - 12ms - ::1
[warn] 2025-10-21 21:39:46: POST /api/auth/login 401 - 8ms - ::1
[error] 2025-10-21 21:39:47: DELETE /api/posts/999 500 - 45ms - ::1
```

No need to manually log requests - it happens automatically!

## 🎯 Best Practices

1. **Use appropriate levels**
   - `info` for successful operations
   - `warn` for recoverable issues
   - `error` for failures that need attention
   - `debug` for troubleshooting

2. **Add context**
   ```javascript
   // Good
   logger.info(`File uploaded by user ${userId}: ${filename}`);
   
   // Better
   logger.info("File uploaded", { userId, filename, size, mimeType });
   ```

3. **Log important events**
   - User authentication
   - Database operations
   - External API calls
   - Business logic milestones

4. **Don't log sensitive data**
   ```javascript
   // ❌ Bad
   logger.info("User data:", { password, creditCard });
   
   // ✅ Good
   logger.info("User data:", { username, email, role });
   ```

## 🛠️ Troubleshooting

### No colored output?
Make sure you're running in a terminal that supports colors (most modern terminals do).

### Logs not showing up in files?
Check that the `logs/` directory exists and is writable:
```bash
ls -la logs/
```

### Too many logs?
Increase the log level:
```env
LOG_LEVEL=warn  # Only warnings and errors
```

### Not enough detail?
Decrease the log level:
```env
LOG_LEVEL=debug  # Everything including debug info
```
