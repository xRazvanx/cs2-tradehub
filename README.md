# CS2 TradeHub

A next-generation CS2 trading and gambling platform, designed to bring back the golden era of CS2 trading with modern features and user experience.

## Project Vision

CS2 TradeHub aims to be the ultimate platform for CS2 item trading and gambling, combining the best aspects of classic trading sites like tf2outpost.com with modern features and design principles.

### Core Features

1. **Trading Marketplace**
   - Advanced item listing system
   - Real-time market prices
   - Secure item verification
   - Instant transactions
   - Advanced search and filtering

2. **Gambling System**
   - Provably fair gambling
   - Multiple game modes
   - Instant payouts
   - Transparent results
   - Anti-fraud measures

3. **Community Features**
   - Active Discord server
   - Trading guides
   - Community events
   - Social media integration
   - User reputation system

## Design Philosophy

### Color Scheme
- Dark theme for reduced eye strain
- Primary: #3b82f6 (Blue) - Trust and security
- Secondary: #1e293b (Dark Blue) - Professionalism
- Accent: #8b5cf6 (Purple) - Creativity and excitement
- Success: #22c55e (Green) - Positive actions
- Warning: #f59e0b (Orange) - Important notices
- Error: #ef4444 (Red) - Critical issues

### UI/UX Principles
1. **Modern Design**
   - Clean, minimalist interface
   - Smooth animations and transitions
   - Responsive layout for all devices
   - Custom scrollbar design
   - Parallax effects

2. **User Experience**
   - Intuitive navigation
   - Clear call-to-action buttons
   - Consistent branding
   - Fast loading times
   - Error prevention

3. **Accessibility**
   - High contrast text
   - Proper spacing
   - Keyboard navigation
   - Screen reader support
   - Focus indicators

## Technical Stack

- **Framework**: Next.js 15.3.1
- **Authentication**: NextAuth.js
- **Styling**: Tailwind CSS
- **State Management**: React Hooks
- **API Integration**: Steam Web API

## Project Structure

```
src/
├── app/
│   ├── api/
│   │   └── auth/
│   │       └── [...nextauth]/
│   │           └── route.ts
│   ├── auth/
│   │   └── signin/
│   │       └── page.tsx
│   ├── layout.tsx
│   ├── page.tsx
│   └── globals.css
├── components/
│   ├── AuthButton.tsx
│   └── Providers.tsx
└── public/
    └── steam-logo.svg
```

## Steam API Setup

### Required Credentials

1. **Steam Web API Key**
   - Go to https://steamcommunity.com/dev/apikey
   - Log in with your Steam account
   - Register your domain (use `localhost` for development)
   - Copy the API key

2. **Environment Variables**
   Create a `.env.local` file in the project root with:
   ```
   NEXTAUTH_URL=http://localhost:3002
   NEXTAUTH_SECRET=2gyZ3GDw3LHZQKDhPmPDL3sjREVRXPr8
   STEAM_CLIENT_ID=your-steam-api-key
   STEAM_CLIENT_SECRET=steam_secret_key_123
   ```

   Note: 
   - `NEXTAUTH_URL` should match your development server port (3002 in our case)
   - `NEXTAUTH_SECRET` is a secure random string for session encryption
   - `STEAM_CLIENT_ID` is your Steam Web API key
   - `STEAM_CLIENT_SECRET` can be any secure random string

### Steam API Integration

1. **API Endpoints Used**
   - `https://steamcommunity.com/openid/login` - Authentication
   - `https://api.steampowered.com/ISteamUser/GetPlayerSummaries/v0002` - User info
   - `https://api.steampowered.com/ISteamUser/GetPlayerItems/v0001` - Inventory

2. **Required Permissions**
   - `openid` - For Steam login
   - `profile` - For user profile data
   - `inventory` - For CS2 items

3. **Rate Limits**
   - 100,000 calls per day
   - 1 call per second per IP
   - Cache responses when possible

## Troubleshooting & Development Notes

### Important Dependencies
- Next.js 15.3.1 (specific version to avoid compatibility issues)
- next-auth@4.24.5 (specific version for Steam authentication)
- Tailwind CSS (for styling)

### Known Issues & Solutions

1. **Babel Dependencies**
   - We don't need Babel as Next.js 15.3.1 has built-in support for modern JavaScript
   - If you see Babel-related errors, remove these dependencies:
     ```bash
     npm uninstall @babel/runtime @babel/runtime-corejs3 @babel/core @babel/preset-env @babel/plugin-transform-runtime
     ```

2. **Tailwind Configuration**
   - The `border-border` utility class error occurs if Tailwind config is not properly set up
   - Make sure `tailwind.config.js` includes the custom colors:
     ```js
     colors: {
       border: 'var(--border)',
       input: 'var(--input)',
       ring: 'var(--ring)',
       // ... other colors
     }
     ```

3. **NextAuth Configuration**
   - Required environment variables:
     ```
     NEXTAUTH_URL=http://localhost:3002
     NEXTAUTH_SECRET=2gyZ3GDw3LHZQKDhPmPDL3sjREVRXPr8
     STEAM_CLIENT_ID=your-steam-api-key
     STEAM_CLIENT_SECRET=steam_secret_key_123
     ```
   - Make sure to register your domain (localhost) in Steam Web API settings

4. **Port Issues**
   - If port 3000 is in use, Next.js will automatically use the next available port
   - Update NEXTAUTH_URL in .env.local to match the actual port being used

5. **Client Components**
   - Add 'use client' directive to components using:
     - Event handlers (onClick, etc.)
     - React hooks (useState, useEffect, etc.)
     - Browser APIs

### Development Workflow

1. **Starting the Project**
   ```bash
   npm install
   npm run dev
   ```

2. **Cleaning Up**
   - If you encounter build issues:
     ```bash
     rm -r -force .next
     npm install
     npm run dev
     ```

3. **Adding New Features**
   - Create new components in `src/components`
   - Add new pages in `src/app`
   - Update styles in `src/app/globals.css`
   - Configure routes in `src/app/api`

## Future Enhancements

1. **Trading Features**
   - Bulk trading
   - Trade history
   - Price alerts
   - Market analysis tools
   - Automated trading

2. **Gambling Features**
   - More game modes
   - Tournament system
   - Leaderboards
   - Achievement system
   - VIP rewards

3. **Community Features**
   - User profiles
   - Trading guides
   - Community market
   - Reputation system
   - Social features

4. **Technical Improvements**
   - Real-time updates
   - WebSocket integration
   - Mobile app
   - API documentation
   - Performance optimization

## Development Status

- [x] Project setup
- [x] Basic UI design
- [x] Authentication setup
- [ ] Trading system
- [ ] Gambling system
- [ ] Community features
- [ ] Mobile optimization
- [ ] Production deployment

## Getting Started

1. Clone the repository
2. Install dependencies:
   ```bash
   npm install
   ```
3. Create `.env.local` file with:
   ```
   NEXTAUTH_URL=http://localhost:3002
   NEXTAUTH_SECRET=2gyZ3GDw3LHZQKDhPmPDL3sjREVRXPr8
   STEAM_CLIENT_ID=your-steam-api-key
   STEAM_CLIENT_SECRET=steam_secret_key_123
   ```
4. Run the development server:
   ```bash
   npm run dev
   ```

## Contributing

We welcome contributions! Please read our contributing guidelines before submitting pull requests.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
