# EasyLogger

`EasyLogger` is a simple and lightweight PHP class to record log messages into files.  
It helps you organize logs by **date**, **file name**, and **log level** (INFO, ERROR, DEBUG, etc.).

---

## 📦 Installation

Install the package via Composer:

```bash
composer require jairojeffsantos/easy-logger
```

---

## 🚀 Usage

### Import the class

```php
use JairoJeffSantos\EasyLogger;
```

### Create a new log

```php
$id = EasyLogger::newLog('app', 'This is an info message.');
```

This will create a log file in the `logs/` directory:

```
logs/2025-10-02_app.log
```

And the log line will look like:

```
[2025-10-02 14:35:21] [INFO] [651c0a4c59d3e] This is an info message.
```

---

## 🔧 Parameters

```php
EasyLogger::newLog(string $filename, string $message, string $level = 'INFO'): string
```

- **$filename** → Base name for the log file. It will be sanitized.  
  Example: `"app"`, `"payment"`, `"user_activity"`.  
- **$message** → Text to log (string).  
- **$level** → Log level (default: `INFO`). Examples:  
  - `"INFO"` → Routine information  
  - `"ERROR"` → Error messages  
  - `"DEBUG"` → Debugging details  

**Return value:**  
The method returns a **unique ID** for each log entry, which can be useful for tracking.

---

## 🗂 Directory Structure

When you log messages, the following structure will be created automatically:

```
project-root/
├── logs/
│   ├── 2025-10-02_app.log
│   ├── 2025-10-02_payment.log
│   └── ...
```

---

## ⚠️ Error Handling

If the `logs/` directory cannot be created or the log file cannot be written,  
an exception may be thrown.

---

## ✅ Example with different levels

```php
use JairoJeffSantos\EasyLogger;

// Info log
EasyLogger::newLog('app', 'Application started.');

// Error log
EasyLogger::newLog('app', 'Failed to connect to database', 'ERROR');

// Debug log
EasyLogger::newLog('app', 'User object: ' . json_encode($user), 'DEBUG');
```

---

## 📄 License

MIT License. Free to use, modify, and distribute.
