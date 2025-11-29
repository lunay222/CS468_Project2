# How to Shut Down and Restart the Study Coach App

## Shutting Down

### 1. Stop Docker Containers (Backend Services)
```bash
cd <your-project-location>
docker-compose down
```

This stops:
- API Gateway (port 8000)
- OCR Service (port 8001)
- Ollama LLM Service (port 11434)

### 2. Stop Mobile App (Expo)
If you have Expo running in a terminal:
- Press `Ctrl+C` in the terminal where `npm start` or `expo start` is running
- Or close the terminal window

## Restarting Later

### 1. Start Backend Services
```bash
cd <your-project-location>
docker-compose up -d
```

The `-d` flag runs containers in the background (detached mode).

### 2. Verify Backend is Running
```bash
# Check container status
docker-compose ps

# Test the API
curl http://localhost:8000/health
```

You should see: `{"status":"healthy","services":{"ocr":"healthy","llm":"healthy"}}`

### 3. Start Mobile App
```bash
cd <your-project-location>/mobile-app
npm start
```

Or:
```bash
cd <your-project-location>/mobile-app
npx expo start
```

### 4. Connect Your Phone
- Scan the QR code that appears in the terminal
- Or use the Expo Go app to connect

## Quick Commands Reference

### Shutdown Everything
```bash
# Stop Docker
docker-compose down

# Stop Expo (press Ctrl+C in the terminal)
```

### Restart Everything
```bash
# Start Docker (in project root)
docker-compose up -d

# Start Expo (in mobile-app directory)
cd mobile-app && npm start
```

## Troubleshooting

### If Docker won't start:
```bash
# Check if Docker Desktop is running
# On Mac: Check the Docker icon in the menu bar

# Restart Docker Desktop if needed
```

### If ports are already in use:
```bash
# Check what's using the ports
lsof -i :8000  # API Gateway
lsof -i :8001  # OCR Service
lsof -i :11434 # Ollama
lsof -i :8081  # Expo

# Stop the processes using those ports
```

### If containers won't start:
```bash
# View logs to see what's wrong
docker-compose logs

# Restart specific service
docker-compose restart api-gateway
```

## Notes

- **Docker containers persist data**: Your Ollama model and any data will be saved in Docker volumes
- **Expo doesn't persist**: You'll need to restart it each time
- **IP Address**: If your computer's IP changes, update it in the mobile app settings

