# CC's Birthday Guide Website

A special birthday guide website with user and admin sides, featuring phase-based content reveals and real-time synchronization.

## Features

### User Side (index.html)
- **Login**: Enter birthday `07/31/2008` to access the user experience
- **Birthday Letter**: Initial letter with video placeholder
- **Welcome Page**: Scroll-style welcome message
- **Spin Wheel**: Hourly spin wheel with prizes (top-right corner)
- **Phase Transitions**: Content revealed based on admin-controlled phases
  - Phase 2: "You can open your shoes now!"
  - Phase 3: Lunch letter
  - Phase 4: Shopping letter with live budget tracker

### Admin Side (admin.html)
- **Access**: Enter birthday `08/24/2006` to access admin panel
- **Phase Control**: Buttons to trigger phases 2, 3, and 4
- **Budget Tracking**: Track shopping budget with real-time updates

## Technical Setup

### Supabase Configuration
- **Project URL**: `https://bqrmdpuknvatplszalkz.supabase.co`
- **Table**: `phases` with columns `id` (int) and `current` (int)
- **Row-level security**: Enabled with proper policies

### Database Schema
```sql
CREATE TABLE phases (
  id INTEGER PRIMARY KEY,
  current INTEGER DEFAULT 1
);

-- Insert initial row
INSERT INTO phases (id, current) VALUES (1, 1);
```

## Files Structure
- `index.html` - Main user experience
- `admin.html` - Admin control panel
- `kitty-bg.jpg` - Background image for welcome section
- `scroll.png` - Scroll background for welcome text

## Key Features Fixed

1. **Supabase Loading**: Script now loads before client initialization
2. **Constants**: Properly initialized at the top of scripts
3. **Phase Syncing**: Real-time updates using Supabase subscriptions
4. **Spin Wheel Timing**: Respects 1-hour rule with localStorage persistence
5. **Budget Tracking**: Live budget tracker in phase 4 with localStorage sync

## Usage

1. **Setup**: Ensure Supabase table is created with initial row
2. **User Access**: Navigate to index.html and enter birthday `07/31/2008`
3. **Admin Access**: Enter birthday `08/24/2006` to access admin panel
4. **Phase Control**: Use admin panel to trigger phases as the day progresses
5. **Budget Tracking**: Both admin and user can track shopping budget in phase 4

## Real-time Features

- Phase changes sync instantly between admin and user
- Budget tracking persists across sessions
- Spin wheel timing respects hourly limits
- All state is properly managed with error handling

## Browser Compatibility

- Modern browsers with ES6+ support
- Requires internet connection for Supabase real-time features
- LocalStorage used for offline state persistence 