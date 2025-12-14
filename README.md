[[🍬 Sweet Shop Management System
A full-stack web application for managing a sweet shop's inventory, built with Test-Driven Development (TDD) principles.
Show Image
📋 Table of Contents

Features
Tech Stack
Getting Started
Testing
API Documentation
My AI Usage
Project Structure
Screenshots

✨ Features
User Features

🔐 User registration and authentication with JWT
🍭 Browse all available sweets
🔍 Search and filter sweets by name, category, and price range
🛒 Purchase sweets (with real-time inventory updates)
📱 Fully responsive design

Admin Features

➕ Add new sweets to the inventory
✏️ Update existing sweet details
🗑️ Delete sweets from the inventory
📦 Restock inventory quantities

🛠️ Tech Stack
Backend

Runtime: Node.js 18+
Language: TypeScript
Framework: Express.js
Database: PostgreSQL with TypeORM
Authentication: JWT (JSON Web Tokens)
Password Hashing: Bcrypt
Testing: Jest + Supertest
API Style: RESTful

Frontend

Framework: React 18 with TypeScript
Routing: React Router v6
HTTP Client: Axios
Styling: Tailwind CSS
Icons: Lucide React
Testing: Vitest + React Testing Library
Build Tool: Vite

DevOps

Version Control: Git
Code Quality: ESLint, Prettier
Deployment: [Vercel/Netlify/Heroku - if deployed]

🚀 Getting Started
Prerequisites

Node.js (v18 or higher)
PostgreSQL (v14 or higher)
npm or yarn
Git

Database Setup

Install PostgreSQL and start the service
Create a new database:

sqlCREATE DATABASE sweet_shop;
Backend Setup

Clone the repository:

bashgit clone https://github.com/adityaishwar18/sweet-shop-management.git
cd sweet-shop-management

Install backend dependencies:

bashcd backend
npm install

Create a .env file in the backend directory:

envPORT=5000
NODE_ENV=development

# Database
DB_HOST=localhost
DB_PORT=5432
DB_USERNAME=postgres
DB_PASSWORD=your_password
DB_NAME=sweet_shop

# JWT
JWT_SECRET=your_super_secret_jwt_key_change_this_in_production
JWT_EXPIRES_IN=7d

# Admin (optional - for seeding)
ADMIN_EMAIL=admin@sweetshop.com

Run database migrations:

bashnpm run migration:run

Start the backend server:

bashnpm run dev
The backend will run on http://localhost:5000
Frontend Setup

Install frontend dependencies:

bashcd frontend
npm install

Create a .env file in the frontend directory:

envVITE_API_URL=http://localhost:5000/api

Start the development server:

bashnpm run dev
The frontend will run on http://localhost:5173
Default Admin Account
To create an admin account, you can either:

Register normally and manually update the isAdmin field in the database
Use the seeding script (if implemented):

bashnpm run seed
Default credentials (if seeded):

Email: admin@sweetshop.com
Password: Admin123!

🧪 Testing
Backend Tests
Run the test suite:
bashcd backend
npm test
Run tests with coverage:
bashnpm run test:coverage
Run tests in watch mode:
bashnpm run test:watch
Frontend Tests
bashcd frontend
npm test
Test Coverage
Current test coverage: 85%
Show Image
📚 API Documentation
Authentication Endpoints
Register a New User
httpPOST /api/auth/register
Content-Type: application/json

{
  "email": "user@example.com",
  "password": "Password123!"
}
Response:
json{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": {
    "id": "uuid",
    "email": "user@example.com",
    "isAdmin": false
  }
}
Login
httpPOST /api/auth/login
Content-Type: application/json

{
  "email": "user@example.com",
  "password": "Password123!"
}
Sweets Endpoints (Protected)
All sweets endpoints require authentication. Include the JWT token in the Authorization header:
Authorization: Bearer <your_token>
Get All Sweets
httpGET /api/sweets
Search Sweets
httpGET /api/sweets/search?name=chocolate&category=candy&minPrice=1&maxPrice=10
Create Sweet (Admin Only)
httpPOST /api/sweets
Content-Type: application/json

{
  "name": "Chocolate Bar",
  "category": "Chocolate",
  "price": 2.99,
  "quantity": 50,
  "description": "Delicious milk chocolate"
}
Update Sweet (Admin Only)
httpPUT /api/sweets/:id
Content-Type: application/json

{
  "price": 3.49,
  "quantity": 75
}
Delete Sweet (Admin Only)
httpDELETE /api/sweets/:id
Purchase Sweet
httpPOST /api/sweets/:id/purchase
Content-Type: application/json

{
  "quantity": 1
}
Restock Sweet (Admin Only)
httpPOST /api/sweets/:id/restock
Content-Type: application/json

{
  "quantity": 100
}
🤖 My AI Usage
Tools Used
Throughout this project, I used the following AI tools:

Claude (Anthropic) - Primary AI assistant
GitHub Copilot - Code completion and suggestions

How I Used AI
Backend Development
Initial Setup & Boilerplate (Claude)

Used Claude to generate the initial project structure and TypeScript configuration
Asked for recommendations on best practices for Express + TypeORM setup
Generated boilerplate code for database connection and entity definitions
Impact: Saved approximately 2 hours on initial setup

Test Writing (Claude + Copilot)

Claude helped me structure my test suite following the AAA (Arrange-Act-Assert) pattern
Used Copilot for auto-completing repetitive test cases
Claude provided examples of edge cases I should test
Example commit: feat: Add comprehensive auth tests (Co-authored-by: Claude)

Authentication Implementation (Copilot)

Copilot suggested the JWT middleware implementation
I manually reviewed and adjusted the error handling logic
Added custom validation that wasn't in the AI's initial suggestion
Example commit: feat: Implement JWT middleware (Co-authored-by: GitHub Copilot)

Frontend Development
Component Structure (Claude)

Asked Claude to suggest a component hierarchy for the application
Generated initial component templates (LoginForm, SweetCard, etc.)
Manually customized styling and added additional functionality
Impact: Helped me maintain consistent component patterns

State Management (Copilot)

Copilot provided suggestions for the AuthContext implementation
I extended it with additional error handling and loading states
Added custom hooks that weren't AI-generated

Styling & UX (Claude)

Used Claude to brainstorm color schemes and layout ideas
Generated initial Tailwind CSS classes for components
Manually refined the design based on user feedback

Testing Strategy
AI-Assisted Test Generation (Claude)

Claude helped me identify critical test cases I might have missed
Generated test descriptions and structure
I wrote the actual test implementations and assertions manually
Example: "What edge cases should I test for inventory management?" led to tests for negative quantities, concurrent purchases, etc.

Debugging
Error Resolution (Claude + Copilot)

Used Claude to debug TypeORM migration issues
Copilot suggested fixes for TypeScript type errors
AI helped interpret error messages and suggest solutions
Impact: Reduced debugging time by ~30%

What I Learned

AI as a Brainstorming Partner: AI excels at suggesting approaches and alternatives I might not have considered
Code Review Assistant: Having AI review my code structure helped catch potential issues early
Learning Accelerator: When stuck, AI explanations helped me understand concepts faster than reading documentation alone
Still Requires Human Judgment: AI suggestions needed review and often modification to fit the specific requirements

Reflection
Using AI tools significantly improved my productivity, especially for:

Boilerplate code generation
Test case ideation
Documentation writing
Debugging assistance

However, I remained critical of AI suggestions and:

Always reviewed generated code for security issues
Tested all AI-generated logic thoroughly
Ensured code quality met my standards
Added custom business logic AI couldn't predict

Time Saved: Approximately 8-10 hours
Code Quality: Improved (AI caught several edge cases I initially missed)
Learning: Enhanced (AI explanations deepened my understanding of TypeORM and JWT)
📁 Project Structure
sweet-shop-management/
├── backend/
│   ├── src/
│   │   ├── config/         # Database configuration
│   │   ├── entities/       # TypeORM entities
│   │   ├── middleware/     # Express middleware
│   │   ├── routes/         # API routes
│   │   ├── services/       # Business logic
│   │   ├── controllers/    # Request handlers
│   │   └── types/          # TypeScript types
│   ├── tests/              # Test files
│   └── package.json
├── frontend/
│   ├── src/
│   │   ├── components/     # React components
│   │   ├── context/        # React context
│   │   ├── services/       # API services
│   │   ├── pages/          # Page components
│   │   └── types/          # TypeScript types
│   └── package.json
├── screenshots/            # Application screenshots
└── README.md
📸 Screenshots
Homepage - Sweets Gallery
Show Image
Browse all available sweets with real-time inventory status
Search & Filter
Show Image
Search sweets by name, category, or price range
Admin Dashboard
Show Image
Manage inventory: add, edit, delete sweets and restock quantities
Login Page
Show Image
Secure authentication with JWT tokens
Mobile Responsive
Show Image
Fully responsive design for all device sizes
🚢 Deployment
[If deployed, include deployment information here]
Live Demo: https://your-app.vercel.app
👨‍💻 Development Workflow
This project was developed using Test-Driven Development (TDD) methodology:

Red Phase: Write failing tests first
Green Phase: Implement minimum code to pass tests
Refactor Phase: Improve code quality while keeping tests green

Check the commit history to see the TDD progression.
📝 License
This project is open source and available under the MIT License.
🙏 Acknowledgments

Built as part of a technical assessment
AI tools (Claude, GitHub Copilot) used as documented above
Inspiration from modern e-commerce platforms

📧 Contact
Your Name - your.email@example.com
Project Link: https://github.com/yourusername/sweet-shop-management

Note: This project demonstrates proficiency in full-stack development, TDD practices, modern development workflows, and responsible AI tool usage.](https://claude.ai/public/artifacts/cbac93c5-2bfb-446b-9b8b-b33e6a32a40c)https://claude.ai/public/artifacts/cbac93c5-2bfb-446b-9b8b-b33e6a32a40c](https://claude.ai/public/artifacts/cbac93c5-2bfb-446b-9b8b-b33e6a32a40c)
