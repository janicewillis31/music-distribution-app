# Music Distribution App - Contributing Guide

## Getting Started

### Prerequisites
- Node.js 18+
- PostgreSQL 14+
- Docker & Docker Compose (optional)
- Git

### Local Development Setup

1. **Clone the repository**
```bash
git clone https://github.com/janicewillis31/music-distribution-app.git
cd music-distribution-app
```

2. **Setup Backend**
```bash
cd backend
npm install
cp .env.example .env
# Edit .env with your configuration
npm run migrate
npm run dev
```

3. **Setup Frontend**
```bash
cd ../frontend
npm install
cp .env.example .env
npm run dev
```

4. **Access the Application**
- Frontend: http://localhost:3000
- Backend API: http://localhost:5000
- API Docs: http://localhost:5000/api/docs (when implemented)

## Development Workflow

### Creating a Feature

1. **Create a feature branch**
```bash
git checkout -b feature/your-feature-name
```

2. **Make your changes**
```bash
# Make commits with clear messages
git commit -m "feat: add new feature"
```

3. **Push to remote**
```bash
git push origin feature/your-feature-name
```

4. **Create a Pull Request**
- Go to GitHub and create a PR
- Fill out the PR template
- Request reviewers

### Commit Message Convention

Use conventional commits:
- `feat:` - New feature
- `fix:` - Bug fix
- `docs:` - Documentation
- `style:` - Code style (formatting)
- `refactor:` - Code refactoring
- `test:` - Test additions/changes
- `chore:` - Build/dependency updates

### Code Style

#### Backend
- Run `npm run lint` to check code style
- Run `npm run lint:fix` to fix issues
- Use `npm run format` to format code

#### Frontend
- ESLint configuration for React
- Prettier for code formatting
- Follow Material-UI component guidelines

## Testing

### Backend Tests
```bash
cd backend
npm test                    # Run tests
npm test -- --watch       # Watch mode
npm test -- --coverage    # Coverage report
```

### Frontend Tests
```bash
cd frontend
npm test                   # Run tests
npm test -- --ui          # UI mode
```

## Database Migrations

### Create a Migration
```bash
cd backend
npm run migrate:create migration_name
```

### Run Migrations
```bash
npm run migrate
```

### Rollback
```bash
npm run migrate:rollback
```

## API Documentation

### Documenting Endpoints

Add JSDoc comments to your controllers:

```javascript
/**
 * POST /api/music/upload
 * @description Upload a new music file
 * @param {string} title - Track title
 * @param {File} audio - Audio file
 * @returns {Object} Created music object
 */
export const uploadMusic = async (req, res) => {
  // Implementation
}
```

## Performance Optimization

### Frontend
- Use React.memo for component optimization
- Lazy load components with React.lazy()
- Optimize images with proper formats
- Use Redux selectors to prevent unnecessary renders

### Backend
- Use database indexes on frequently queried columns
- Implement caching with Redis
- Use connection pooling for database
- Compress API responses with gzip

## Security Guidelines

1. **Never commit secrets**
   - Use .env files
   - Don't hardcode API keys
   - Rotate credentials regularly

2. **Input Validation**
   - Validate all user inputs
   - Use Yup or similar for schema validation
   - Sanitize file uploads

3. **Authentication & Authorization**
   - Use JWT tokens
   - Implement role-based access control
   - Never store plain passwords

4. **API Security**
   - Use HTTPS in production
   - Implement rate limiting
   - Use CORS properly
   - Validate headers

## Troubleshooting

### Database Connection Issues
```bash
# Check PostgreSQL is running
psql -U username -d database_name

# Reset database
npm run migrate:reset
```

### Port Already in Use
```bash
# Linux/Mac
lsof -i :5000
kill -9 <PID>

# Windows
netstat -ano | findstr :5000
taskkill /PID <PID> /F
```

### Dependencies Issues
```bash
# Clear cache and reinstall
rm -rf node_modules package-lock.json
npm install
```

## Pull Request Process

1. Update the README with new features
2. Update version in package.json following semver
3. Ensure all tests pass
4. Get approval from at least 1 reviewer
5. Merge only after CI passes

## Questions?

Create an issue or ask in discussions!

## License

This project is licensed under MIT License - see LICENSE file for details.
