# Havilla - Venue Booking Application

A comprehensive mobile application for venue browsing, booking management, calendar availability, and quote requests. Built with React Native and Expo.

## Overview

Havilla is a mobile-first platform that enables users to:
- Browse and discover available venues
- Manage bookings efficiently
- Check calendar availability in real-time
- Request and manage quotes
- Track booking history

## Tech Stack

### Frontend
- **React Native**: 0.81.5
- **React**: 19.1.0
- **Expo**: ~54.0.34
- **Expo Router**: ~6.0.23 (File-based routing)
- **TypeScript**: ~5.9.2

### Navigation & UI
- **React Navigation**: 7.x
  - Bottom Tabs Navigation
  - Stack Navigation
  - Native Navigation Support
- **React Native Vector Icons**: ^15.0.3
- **React Native Safe Area Context**: ~5.6.0
- **React Native Screens**: ~4.16.0

### State Management & Storage
- **Zustand**: ^5.0.14 (Lightweight state management)
- **Async Storage**: 2.2.0 (Local data persistence)
- **Expo Secure Store**: ~15.0.8 (Secure credential storage)

### Backend & Database
- **Supabase**: ^2.39.3 (PostgreSQL database, Auth, Real-time)

### Utilities & Features
- **React Native Calendars**: ^1.1314.0 (Calendar UI component)
- **Expo Notifications**: ~0.32.17 (Push notifications)
- **Expo Device**: ~8.0.10 (Device information)
- **Expo Font**: ~14.0.11 (Custom fonts)
- **Expo Linking**: ~8.0.12 (Deep linking)
- **Expo Web Browser**: ~15.0.11 (Web browsing in-app)
- **Expo Status Bar**: ~3.0.9 (Status bar management)
- **Expo Constants**: ~18.0.13 (App constants)
- **Expo Splash Screen**: ~31.0.13 (Splash screen management)
- **React Native Reanimated**: ~4.1.1 (Animations)
- **React Native Worklets**: 0.5.1 (Background tasks)

### Development Tools
- **TypeScript**: ^5.9.2
- **React Test Renderer**: 19.1.0

## Project Structure

```
Havilla-app/
├── havilla/                      # Main application directory
│   ├── app/                      # Expo Router pages (file-based routing)
│   ├── assets/                   # Images, fonts, and other static assets
│   │   ├── images/
│   │   │   ├── icon.png
│   │   │   ├── splash-icon.png
│   │   │   ├── adaptive-icon.png
│   │   │   └── favicon.png
│   ├── components/               # Reusable React components
│   ├── services/                 # API and service integrations
│   ├── hooks/                    # Custom React hooks
│   ├── store/                    # Zustand store configuration
│   ├── utils/                    # Utility functions
│   ├── types/                    # TypeScript type definitions
│   ├── constants/                # App constants
│   ├── app.json                  # Expo configuration
│   ├── package.json              # Dependencies and scripts
│   ├── tsconfig.json             # TypeScript configuration
│   └── expo-env.d.ts             # Expo environment types
├── README.md                     # Project documentation
└── .gitattributes                # Git configuration
```

## Getting Started

### Prerequisites
- Node.js >= 16.x
- npm or yarn
- Expo CLI: `npm install -g expo-cli`
- iOS Simulator (Mac) or Android Emulator

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/Johnnie-kay/Havilla-app.git
   cd Havilla-app/havilla
   ```

2. **Install dependencies**
   ```bash
   npm install
   # or
   yarn install
   ```

3. **Set up environment variables**
   Create a `.env.local` file in the `havilla/` directory with your Supabase credentials:
   ```
   EXPO_PUBLIC_SUPABASE_URL=your_supabase_url
   EXPO_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
   ```

4. **Start the development server**
   ```bash
   npm start
   ```

### Available Scripts

| Script | Description |
|--------|-------------|
| `npm start` | Start Expo development server |
| `npm run android` | Start on Android emulator |
| `npm run ios` | Start on iOS simulator |
| `npm run web` | Start in web browser |

## 🔌 API Integration

### Backend Service: Supabase

The application uses **Supabase** for:
- **Authentication**: User login/signup
- **Database**: PostgreSQL for data persistence
- **Real-time**: Real-time database subscriptions
- **Storage**: File storage for venue images

### API Service Architecture

Services are typically located in `app/services/` and handle:
- Supabase client initialization
- API request/response handling
- Error management
- Data transformation

### Core APIs

#### User Authentication
```typescript
// Login/Signup through Supabase Auth
```

#### Venue Management
- **List Venues**: Fetch all available venues
- **Venue Details**: Get detailed information about a specific venue
- **Search Venues**: Search venues by location, amenities, capacity
- **Venue Ratings**: View and submit venue reviews

#### Bookings
- **Create Booking**: Submit a new venue booking
- **View Bookings**: List user's bookings
- **Cancel Booking**: Cancel an existing booking
- **Modify Booking**: Update booking details

#### Calendar & Availability
- **Check Availability**: Query venue availability for dates
- **Blocked Dates**: View blocked/unavailable dates
- **Availability Calendar**: Visual calendar of availability

#### Quote Requests
- **Submit Quote Request**: Send quote request for venue
- **View Quotes**: List received quotes
- **Accept/Reject Quotes**: Manage quote responses
- **Quote History**: Track quote requests and responses

## UI/UX Components

### Navigation Structure
- **Bottom Tab Navigation**: Primary navigation for main screens
- **Stack Navigation**: Secondary navigation within tabs
- **Modal Navigation**: For dialogs and overlays

### Key Screens
- **Home/Discover**: Browse venues
- **Search**: Find venues with filters
- **Bookings**: Manage user bookings
- **Calendar**: View availability
- **Profile**: User account settings
- **Notifications**: Booking and quote updates

## Security Features

- **Expo Secure Store**: Store sensitive data (tokens, passwords)
- **Supabase Authentication**: Secure user authentication
- **Environment Variables**: Hide sensitive configuration
- **HTTPS**: All API communications encrypted

## Features

### Core Features
- ✅ Venue Discovery & Browsing
- ✅ Real-time Availability Checking
- ✅ Booking Management
- ✅ Quote Request System
- ✅ Calendar Integration
- ✅ Push Notifications
- ✅ User Authentication
- ✅ Booking History

## Testing

The project includes testing setup with React Test Renderer. To run tests:

```bash
npm test
```

## Build & Deployment

### Build for Production

**iOS:**
```bash
expo build:ios
```

**Android:**
```bash
expo build:android
```

**Web:**
```bash
expo build:web
```

### Deploy
- iOS apps are published to Apple App Store
- Android apps are published to Google Play Store
- Web version can be deployed to static hosting

## State Management with Zustand

The app uses Zustand for lightweight state management. Store files are typically located in `app/store/`.

### Store Usage Example
```typescript
// Define store
import { create } from 'zustand';

const useBookingStore = create((set) => ({
  bookings: [],
  addBooking: (booking) => set((state) => ({
    bookings: [...state.bookings, booking]
  }))
}));

// Use in components
const { bookings, addBooking } = useBookingStore();
```

## Local Storage

- **Async Storage**: Stores user preferences, cache data
- **Secure Store**: Stores authentication tokens, passwords

## Deep Linking

The app supports deep linking through Expo Linking. Deep links use the `havilla://` scheme.

## Platform Support

- **iOS**: 12.0 or later (with Tablet support)
- **Android**: API 21+ (with edge-to-edge and adaptive icons)
- **Web**: Chrome, Safari, Firefox (modern browsers)

## Configuration

### Expo Configuration (`app.json`)
- App name: "havilla"
- Orientation: Portrait
- Theme: Automatic (follows system settings)
- New Architecture: Enabled
- Typed Routes: Enabled

### TypeScript Configuration
- Strict mode enabled
- Path aliases: `@/*` maps to root directory
- Expo types included

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Feature update'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is private. See the repository for license details.

## Team

- **Repository Owner**: [Johnnie-kay](https://github.com/Johnnie-kay)
- **Original Source**: [kingvado1/Havilla-app](https://github.com/kingvado1/Havilla-app)

## Support & Contact

For issues, feature requests, or questions:
- Open an issue on GitHub
- Contact the development team

## Additional Resources

- [Expo Documentation](https://docs.expo.dev/)
- [React Native Documentation](https://reactnative.dev/)
- [Supabase Documentation](https://supabase.com/docs)
- [React Navigation Docs](https://reactnavigation.org/)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)

---

**Last Updated**: June 5, 2026
**Version**: 1.0.0
**Status**: Active Development
