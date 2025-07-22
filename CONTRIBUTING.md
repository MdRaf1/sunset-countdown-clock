# Contributing to Sunset Countdown Clock

Thank you for your interest in contributing to the Sunset Countdown Clock! This document provides guidelines and information for contributors.

## Code of Conduct

By participating in this project, you agree to abide by our code of conduct:

- Be respectful and inclusive
- Focus on constructive feedback
- Help create a welcoming environment for all contributors
- Report any unacceptable behavior to the project maintainers

## How to Contribute

### Reporting Issues

1. **Search existing issues** first to avoid duplicates
2. **Use clear, descriptive titles** for new issues
3. **Provide detailed information** including:
   - Browser and version
   - Operating system
   - Steps to reproduce
   - Expected vs actual behavior
   - Screenshots if applicable

### Suggesting Features

1. **Check existing feature requests** to avoid duplicates
2. **Describe the feature** in detail with use cases
3. **Explain the benefits** and potential impact
4. **Consider backward compatibility** implications

### Pull Requests

1. **Fork the repository** and create a feature branch
2. **Follow coding standards** outlined below
3. **Write clear commit messages** following conventional commits
4. **Include tests** for new functionality
5. **Update documentation** as needed
6. **Ensure all checks pass** before submitting

## Development Setup

### Prerequisites

- Modern web browser with developer tools
- Text editor or IDE
- Local web server (Python, Node.js, or similar)

### Getting Started

```bash
# Clone your fork
git clone https://github.com/MdRaf1/sunset-countdown-clock.git
cd sunset-countdown-clock

# Create a feature branch
git checkout -b feature/your-feature-name

# Start local development server
python -m http.server 8000
# or
npx serve .
```

### Testing

The application includes comprehensive debugging tools:

```javascript
// Access debug API in browser console
const debug = window.sunsetClock.debug;

// Test functionality
debug.getState();
debug.getPerformanceStats();
debug.getBrowserSupport();
```

## Coding Standards

### JavaScript Style

- **ES6+ Features**: Use modern JavaScript with fallbacks
- **Consistent Formatting**: Use 4 spaces for indentation
- **Clear Naming**: Use descriptive variable and function names
- **Comments**: Include JSDoc comments for classes and public methods
- **Error Handling**: Always include proper error handling

### Code Organization

- **Separation of Concerns**: Keep classes focused on single responsibilities
- **Plugin Architecture**: Use the plugin system for extensions
- **State Management**: Use the reactive state system appropriately
- **Performance**: Consider performance implications of changes

### Example Code Style

```javascript
/**
 * Example class demonstrating coding standards
 */
class ExamplePlugin {
    constructor(options = {}) {
        this.options = {
            defaultValue: true,
            ...options
        };
        this.initialized = false;
    }
    
    /**
     * Initialize the plugin
     * @param {SunsetClockManager} clockManager - The clock manager instance
     */
    install(clockManager) {
        if (this.initialized) {
            console.warn('Plugin already initialized');
            return;
        }
        
        try {
            this.setupPlugin(clockManager);
            this.initialized = true;
            console.log('Example plugin initialized');
        } catch (error) {
            console.error('Failed to initialize plugin:', error);
        }
    }
    
    setupPlugin(clockManager) {
        // Implementation here
    }
}
```

## Architecture Guidelines

### Adding New Features

1. **Plugin System**: Consider if the feature can be implemented as a plugin
2. **State Management**: Use the reactive state system for data that changes
3. **Error Boundaries**: Ensure proper error handling and recovery
4. **Accessibility**: Include ARIA attributes and keyboard support
5. **Performance**: Monitor performance impact with included tools

### Security Considerations

- **Input Sanitization**: Always sanitize user inputs
- **XSS Prevention**: Avoid innerHTML with user data
- **Privacy Protection**: Respect user privacy (location data)
- **Rate Limiting**: Implement appropriate rate limiting

### Testing New Features

1. **Manual Testing**: Test in multiple browsers
2. **Accessibility Testing**: Use screen readers and keyboard navigation
3. **Performance Testing**: Monitor with built-in performance tools
4. **Error Testing**: Test error conditions and recovery

## Commit Message Guidelines

Follow conventional commit format:

```text
type(scope): description

[optional body]

[optional footer]
```

### Types

- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, etc.)
- `refactor`: Code refactoring
- `perf`: Performance improvements
- `test`: Adding or updating tests
- `chore`: Build process or auxiliary tool changes

### Examples

```text
feat(themes): add ocean theme with animated transitions

Add new ocean-inspired theme with blue and teal gradients.
Includes smooth animations between theme transitions.

Closes #123
```

```text
fix(geolocation): handle timeout errors gracefully

Improve error handling for geolocation timeouts by
implementing exponential backoff retry logic.

Fixes #456
```

## Documentation

### Code Documentation

- **JSDoc Comments**: Use for all public methods and classes
- **Inline Comments**: Explain complex logic and workarounds
- **README Updates**: Update README for new features or changes
- **Architecture Docs**: Update architecture documentation as needed

### Documentation Style

```javascript
/**
 * Calculate time remaining until sunset
 * @param {Date} targetSunset - The target sunset time
 * @param {Date} [currentTime=new Date()] - Current time for calculation
 * @returns {number} Time difference in milliseconds
 * @throws {Error} When targetSunset is invalid
 */
static calculateTimeRemaining(targetSunset, currentTime = new Date()) {
    if (!(targetSunset instanceof Date)) {
        throw new Error('Invalid targetSunset provided');
    }
    return targetSunset.getTime() - currentTime.getTime();
}
```

## Performance Guidelines

### Best Practices

- **Minimize DOM Manipulation**: Batch DOM updates when possible
- **Memory Management**: Clean up event listeners and intervals
- **Efficient Calculations**: Cache expensive calculations
- **Monitoring**: Use built-in performance monitoring tools

### Performance Testing

```javascript
// Use built-in performance monitoring
const debug = window.sunsetClock.debug;
const stats = debug.getPerformanceStats();
console.log('Performance metrics:', stats);
```

## Security Guidelines

### Input Validation

```javascript
// Always validate and sanitize inputs
function sanitizeInput(input) {
    if (typeof input !== 'string') return '';
    return input.replace(/<script\b[^<]*(?:(?!<\/script>)<[^<]*)*<\/script>/gi, '')
                .replace(/<[^>]*>/g, '')
                .substring(0, 200);
}
```

### Privacy Protection

```javascript
// Round coordinates for privacy
function sanitizeCoordinates(lat, lon) {
    return {
        latitude: Math.round(lat * 100) / 100,
        longitude: Math.round(lon * 100) / 100
    };
}
```

## Questions and Support

- **Issues**: Use GitHub issues for bug reports and feature requests
- **Discussions**: Use GitHub discussions for general questions
- **Documentation**: Check the README and inline documentation first

## Recognition

Contributors will be recognized in:

- GitHub contributors list
- Release notes for significant contributions
- README acknowledgments for major features

Thank you for contributing to the Sunset Countdown Clock! 🌅
