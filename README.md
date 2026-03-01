```markdown
# Restaurant App - Flavor

A beautiful restaurant mobile app built with React Native and Expo.

## 🚀 Quick Start

### 1. Install dependencies
```bash
npm install
npm install express
```

### 2. Start the server
```bash
node server.js
```
You'll see: `Server running at http://localhost:3000`

### 3. Find your IP address
Open a new terminal and type:
```bash
ipconfig
```
Look for `IPv4 Address` (like 192.168.0.101)

### 4. Update the IP in app.js
Open **app.js** and change:
```javascript
const SERVER_URL = 'http://localhost:3000';
```
to
```javascript
const SERVER_URL = 'http://YOUR_IP_ADDRESS:3000';
```

### 5. Start the app
```bash
npx expo start
```
Scan the QR code with Expo Go app

## 📱 App Features

- User Login & Registration
- Browse Menu with beautiful images
- Filter by Categories
- Search Dishes
- Add to Cart
- Place Orders
- View Profile

## 🔗 Server URLs

- API Home: `http://YOUR_IP:3000`
- Menu JSON: `http://YOUR_IP:3000/api/menu`

## 👤 Demo Accounts

```
Email: john@example.com
Password: 123456

Email: sarah@example.com
Password: 123456
```

## 📁 Project Files

- `app.js` - Main React Native app
- `server.js` - Backend server with menu data
- `app.json` - Expo configuration

## 🛠️ Technologies

- React Native
- Expo
- Node.js
- Express

## 📝 Notes

- Make sure phone and computer are on same WiFi
- Update IP address in app.js before running
- Server must be running before using the app
```
