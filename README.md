```
# LUMIÈRE - Premium Restaurant Mobile App

A React Native mobile application for a luxury restaurant experience with separate customer and manager interfaces.

## Overview

LUMIÈRE is a full-featured restaurant app that allows customers to browse menus, place orders, make reservations, and earn loyalty points, while providing managers with tools to manage orders, menu items, and reservations.

## Features

### Customer Features
- Browse menu with category filtering and search
- View detailed item information (price, description, ratings, allergens)
- Add items to cart with quantity controls
- Place orders with pickup time selection
- Make table reservations with date/time and party size
- Track loyalty points and tier status
- View order history and current order status

### Manager Features
- Live dashboard with key metrics
- View and manage all orders with status updates
- Add, edit, and delete menu items
- Manage reservation requests (confirm/decline)
- Track revenue and order statistics

## Tech Stack

- React Native (0.72)
- Expo (51.0)
- React Navigation (6.x)
- Expo Linear Gradient
- Ionicons

## Installation

```bash
# Clone repository
git clone <repository-url>
cd lumiere-app

# Install dependencies
npm install

# Start Expo
npx expo start

# Run on specific platforms
npm run ios
npm run android
npm run web
```

## Project Structure

```
lumiere-app/
├── App.js                    # Root component with auth flow
├── assets/                   # Images and assets
└── src/
    ├── components/           # Reusable UI components
    │   ├── Card.js
    │   ├── GoldButton.js
    │   ├── Header.js
    │   ├── LuxInput.js
    │   ├── Sheet.js
    │   └── Badge.js
    ├── screens/              # Screen components
    │   ├── AuthScreen.js
    │   ├── Customer/
    │   │   ├── HomeScreen.js
    │   │   ├── ExploreScreen.js
    │   │   ├── ReservationScreen.js
    │   │   ├── CartScreen.js
    │   │   └── ProfileScreen.js
    │   └── Manager/
    │       ├── ManagerDashboard.js
    │       ├── ManagerOrders.js
    │       ├── ManagerMenu.js
    │       └── ManagerReservations.js
    └── navigation/           # Navigation config
        ├── CustomerApp.js
        └── ManagerApp.js
```

## Key Components

### Global State Management
Lightweight pub/sub pattern for state management across components:

```javascript
// Global state object
let G = {
  cart: [],
  loyalty: 1240,
  reservations: [],
  menuItems: [...],
  orders: []
};

// Subscribe to changes
function useGlobal() {
  const [state, setState] = useState(G);
  useEffect(() => {
    _subs.add(setState);
    return () => _subs.delete(setState);
  }, []);
  return [state, updateG];
}
```

### Design Tokens
```javascript
const T = {
  obsidian: '#0A0A0F',
  surface: '#16161F',
  elevated: '#1E1E2A',
  border: '#2A2A3A',
  gold: '#C9A96E',
  goldLight: '#E8C98A',
  cream: '#F5F0E8',
  ghost: '#6B6B80',
  success: '#4ECDA4',
  warning: '#F59E0B',
  danger: '#EF4444'
};
```

## Data Models

### MenuItem
```javascript
{
  id: String,
  name: String,
  subtitle: String,
  price: Number,
  category: String,
  emoji: String,
  image: String,
  tags: Array,
  description: String,
  rating: Number,
  reviews: Number,
  calories: Number,
  prepTime: Number,
  allergens: Array
}
```

### Order
```javascript
{
  id: String,
  customer: String,
  table: String,
  items: Array,
  total: Number,
  status: 'received' | 'preparing' | 'ready' | 'picked up',
  time: String,
  notes: String
}
```

### Reservation
```javascript
{
  id: String,
  name: String,
  date: String,
  time: String,
  partySize: Number,
  occasion: String,
  status: 'pending' | 'confirmed' | 'cancelled'
}
```

## User Flows

### Customer Order Flow
1. Browse menu items by category
2. Add items to cart
3. Review cart and adjust quantities
4. Select pickup time
5. Place order and earn loyalty points
6. Track order status updates
7. Pick up order when ready

### Manager Order Flow
1. View all active orders
2. Filter by status (received, preparing, ready)
3. Select order to view details
4. Update order status
5. Customer receives notification

## Screens

### Customer Screens
- **Auth** - Login/signup with role selection
- **Home** - Greeting, featured items, quick stats
- **Explore** - Menu with categories and search
- **Reserve** - Table booking form
- **Cart** - Order review and checkout
- **Profile** - Loyalty status and settings

### Manager Screens
- **Dashboard** - Key metrics and live orders
- **Orders** - Complete order management
- **Manage Menu** - CRUD operations for menu items
- **Reservations** - Handle booking requests

## API Integration Example

```javascript
// Place order
const placeOrder = () => {
  setLoading(true);
  setTimeout(() => {
    updateG(s => ({
      cart: [],
      loyalty: s.loyalty + Math.floor(total),
      orders: [...s.orders, newOrder]
    }));
    Alert.alert('Order Placed', `Order #${orderId}`);
    setLoading(false);
  }, 1600);
};
```

## Running the App

### Development
```bash
# Start development server
expo start

# Clear cache
expo start -c

# Run on device
expo start --tunnel
```

### Building for Production
```bash
# Android build
expo build:android

# iOS build
expo build:ios
```

## Testing Credentials

### Customer Login
- Email: guest@lumiere.com
- Password: any password works

### Manager Login
- Email: manager@lumiere.com
- Password: any password works

## Dependencies

```json
{
  "react-native": "0.72",
  "expo": "~51.0.0",
  "@react-navigation/native": "^6.0.0",
  "@react-navigation/stack": "^6.0.0",
  "@react-navigation/bottom-tabs": "^6.0.0",
  "expo-linear-gradient": "~13.0.0",
  "@expo/vector-icons": "^14.0.0"
}
```

## Known Issues & Solutions

### Issue: Scroll not working on some screens
**Solution:** Ensure contentContainerStyle is properly set on ScrollView and FlatList components.

### Issue: Images not loading
**Solution:** Using Unsplash placeholder URLs that require internet connection.

## Browser Support

- iOS Safari (iOS 13+)
- Chrome for Android (Android 8+)
- Expo Go app (all platforms)

## Contributing

1. Fork the repository
2. Create feature branch
3. Commit changes
4. Push to branch
5. Open pull request

## License

MIT License - feel free to use this project for learning purposes.

---

**Note**: This is a demonstration project for educational purposes. Images used are from Unsplash and require attribution.
```