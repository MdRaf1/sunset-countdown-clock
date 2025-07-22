# Demo and Examples

This document provides examples and demonstrations of the Sunset Countdown Clock's features.

## Live Demo

Open `index.html` in your browser to see the application in action. The application will:

1. Request your location permission
2. Calculate sunset time for your location
3. Display a real-time countdown
4. Change background themes as sunset approaches

## Feature Demonstrations

### Theme System

The application includes multiple themes that change based on time remaining:

```javascript
// Access the debug API in browser console
const debug = window.sunsetClock.debug;

// Switch to ocean theme
debug.changeTheme('ocean');

// Test different time scenarios
debug.testTheme();
```

### Performance Monitoring

View real-time performance metrics:

```javascript
// Get performance statistics
const stats = debug.getPerformanceStats();
console.log('Average tick time:', stats.tick?.avg, 'ms');

// View current state
const state = debug.getState();
console.log('Minutes remaining:', state.minutesRemaining);
```

### Accessibility Features

- **Keyboard Navigation**: Use `Alt + 1-9` to switch themes, `Escape` for default
- **Screen Reader Support**: ARIA live regions announce countdown updates
- **High Contrast**: Themes work well with high contrast mode

### Error Handling

The application includes comprehensive error handling:

```javascript
// View error history
const errors = debug.getErrorHistory();
console.log('Recent errors:', errors);

// Check browser support
const support = debug.getBrowserSupport();
console.log('Browser features:', support);
```

## Configuration Examples

### Custom Plugin

Create a custom plugin to extend functionality:

```javascript
const CustomPlugin = {
    install(clockManager) {
        console.log('Custom plugin installed');
        
        // Subscribe to state changes
        clockManager.state.subscribe('minutesRemaining', (minutes) => {
            if (minutes === 30) {
                console.log('30 minutes until sunset!');
            }
        });
    },
    
    onTick(state, elements) {
        // Custom logic on each update
    }
};

// Use the plugin
window.sunsetClock.use(CustomPlugin);
```

### Custom Theme

Add a custom theme:

```javascript
// Access theme manager
const themeManager = window.sunsetClock.themeManager;

// Register new theme
themeManager.registerTheme('sunset', {
    gradients: {
        day: 'linear-gradient(to top, #FFE4B5, #FFD700)',
        'pre-sunset': 'linear-gradient(to top, #FF8C00, #FF6347)',
        'golden-hour': 'linear-gradient(to top, #FF4500, #8B0000)',
        night: 'linear-gradient(to top, #2F2F4F, #000080)',
        error: 'linear-gradient(to top, #8B0000, #DC143C)'
    }
});

// Apply the theme
themeManager.applyTheme('sunset');
```

## Browser Compatibility

### Modern Browsers

- Chrome 60+
- Firefox 55+
- Safari 12+
- Edge 79+

### Legacy Support

- Internet Explorer 11 (limited functionality)
- Older mobile browsers (graceful degradation)

## Performance Benchmarks

Typical performance metrics on modern hardware:

- **Initialization**: < 50ms
- **Tick Performance**: < 2ms average
- **Memory Usage**: < 5MB
- **Location Lookup**: < 3 seconds

## Mobile Experience

The application is fully responsive and optimized for mobile:

- Touch-friendly interface
- Responsive typography
- Optimized for various screen sizes
- Minimal data usage

## PWA Features

The application is Progressive Web App ready:

- Service Worker support
- Offline functionality preparation
- App manifest ready
- Installable on mobile devices

## Development Mode

Enable development mode for enhanced debugging:

```javascript
// Development mode provides:
// - Faster update intervals (100ms)
// - Verbose logging
// - Performance monitoring
// - Debug information
```

## Production Deployment

For production deployment:

1. Serve over HTTPS for geolocation support
2. Enable gzip compression
3. Add appropriate CSP headers
4. Consider CDN for SunCalc library

## Troubleshooting

### Common Issues

1. **Location Permission Denied**
   - Application shows error message
   - Fallback functionality available

2. **SunCalc Library Not Loading**
   - Check network connectivity
   - Verify CDN availability

3. **Performance Issues**
   - Check browser console for errors
   - Monitor with built-in performance tools

### Debug Commands

```javascript
// Reset application state
location.reload();

// Clear location cache
localStorage.clear();

// Test without location
// (manual coordinates can be set for testing)
```
