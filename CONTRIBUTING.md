# Contributing to Campus Ride Share

Thank you for your interest in contributing to Campus Ride Share! We welcome contributions from everyone.

## Code of Conduct

Please be respectful and constructive in all interactions.

## How to Contribute

### Reporting Bugs

1. Check if the issue already exists
2. Provide a clear description of the bug
3. Include steps to reproduce
4. Provide your environment details (OS, Node version, etc.)
5. Add screenshots if applicable

### Suggesting Enhancements

1. Clearly describe the enhancement
2. Explain why it would be useful
3. List some examples of how it would work

### Pull Requests

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Make your changes
4. Write/update tests as needed
5. Commit with clear messages
6. Push to your fork
7. Open a Pull Request

## Development Setup

```bash
# Clone and setup
git clone https://github.com/priaaBuilds/campus-ride-share.git
cd campus-ride-share

# Install dependencies
cd backend && npm install
cd ../frontend && npm install

# Start development
cd backend && npm run dev
# In another terminal
cd frontend && npm start
```

## Coding Standards

- Use consistent naming conventions
- Write clear, self-documenting code
- Add comments for complex logic
- Follow the existing code style
- Keep functions small and focused

## Testing

```bash
# Run tests
npm test

# Run tests with coverage
npm run test:coverage

# Watch mode
npm run test:watch
```

## Commit Messages

Use clear, descriptive commit messages:

```
feat: Add new ride matching algorithm
fix: Resolve location tracking bug
docs: Update API documentation
refactor: Optimize database queries
test: Add unit tests for payment service
```

## Questions?

Feel free to open an issue or discussion if you have questions!
