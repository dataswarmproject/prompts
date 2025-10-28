# Software Development Prompts

Professional-grade prompts for developers, engineers, and technical teams.

## Categories

1. [Code Generation](#code-generation)
2. [Code Review](#code-review)
3. [Debugging](#debugging)
4. [Architecture & Design](#architecture-and-design)
5. [Testing](#testing)
6. [Documentation](#documentation)
7. [Refactoring](#refactoring)
8. [Performance Optimization](#performance-optimization)

---

## Code Generation

### Full Stack Feature

```
You are a senior full-stack developer expert in [your tech stack].

Task: Implement a complete feature for [feature description]

Tech Stack:
- Frontend: [e.g., React 18, TypeScript, TailwindCSS]
- Backend: [e.g., Node.js, Express, PostgreSQL]
- Architecture: [e.g., REST API, microservices]

Requirements:
1. [Requirement 1]
2. [Requirement 2]
3. [Requirement 3]

Please provide:
- Backend API endpoints with validation
- Database schema/migrations
- Frontend components with proper typing
- Error handling and edge cases
- Basic unit tests
- API documentation

Follow these conventions:
- [Your code style guide]
- [Naming conventions]
- [Project structure]
```

### API Endpoint

```
Create a REST API endpoint for [purpose]

Specifications:
- Method: [GET/POST/PUT/DELETE]
- Route: [/api/v1/resource]
- Authentication: [JWT/OAuth2/API Key]
- Rate Limiting: [requests per minute]

Input:
```json
{
  "field1": "type",
  "field2": "type"
}
```

Output:
```json
{
  "success": boolean,
  "data": {},
  "error": string | null
}
```

Requirements:
- Input validation with clear error messages
- Database query optimization
- Proper HTTP status codes
- Comprehensive error handling
- OpenAPI/Swagger documentation
- Unit tests

Language: [Python/JavaScript/Go/etc.]
Framework: [FastAPI/Express/Gin/etc.]
```

### Database Schema

```
You are a database architect with expertise in [database type].

Design a database schema for [application description].

Requirements:
- Tables/Collections needed: [list main entities]
- Expected scale: [number of users/records]
- Query patterns: [main queries that need to be fast]
- Relationships: [key relationships]

Provide:
1. Complete schema with proper data types
2. Indexes for performance
3. Foreign keys and constraints
4. Migration script
5. Example queries for common operations
6. Normalization explanation
7. Scalability considerations

Database: [PostgreSQL/MongoDB/MySQL/etc.]
ORM: [SQLAlchemy/Prisma/TypeORM/etc.]
```

### Algorithm Implementation

```
Implement [algorithm name] in [programming language]

Context: [where and why you need this]

Requirements:
- Time complexity: [O(n log n) or better]
- Space complexity: [O(1) if possible]
- Handle edge cases: [empty input, single element, etc.]
- Include comprehensive comments
- Add type hints/annotations
- Provide example usage
- Include unit tests with various cases

Additional constraints:
- [Constraint 1]
- [Constraint 2]

Please also explain:
- Algorithm approach and reasoning
- Why this solution is optimal
- Trade-offs made
```

---

## Code Review

### Comprehensive Review

```
You are a senior engineer conducting a code review.

Review this code focusing on:

1. **Correctness**: Logic errors, edge cases, potential bugs
2. **Performance**: Efficiency, scalability concerns
3. **Security**: Vulnerabilities, input validation, auth issues
4. **Maintainability**: Code clarity, documentation, modularity
5. **Best Practices**: Language idioms, design patterns
6. **Testing**: Test coverage, test quality

Code to review:
```[language]
[paste your code]
```

Context:
- Purpose: [what this code does]
- Part of: [larger system context]
- Performance requirements: [any specific needs]
- Security level: [public-facing, internal, etc.]

Please provide:
- Critical issues (must fix)
- Suggestions (should consider)
- Positive aspects (what's done well)
- Specific code suggestions with examples
```

### Security Audit

```
Perform a security audit on this code:

```[language]
[paste code]
```

Check for:
- Injection vulnerabilities (SQL, XSS, Command)
- Authentication/Authorization flaws
- Sensitive data exposure
- Insecure deserialization
- Cryptographic issues
- Dependency vulnerabilities
- Rate limiting needs
- Input validation gaps

For each issue found:
1. Severity level (Critical/High/Medium/Low)
2. Detailed explanation
3. How to exploit (briefly)
4. How to fix (with code example)
5. Prevention best practices
```

---

## Debugging

### Bug Investigation

```
I'm debugging a problem in my [language/framework] application.

**Symptoms**:
[Describe what's going wrong]

**Error Message**:
```
[Full error message with stack trace]
```

**Relevant Code**:
```[language]
[Code where error occurs]
```

**Environment**:
- OS: [Windows/Mac/Linux]
- Language version: [e.g., Python 3.11]
- Framework version: [e.g., Django 4.2]
- Dependencies: [relevant packages]

**What I've Tried**:
1. [Attempt 1 and result]
2. [Attempt 2 and result]

**Expected Behavior**:
[What should happen]

**Actual Behavior**:
[What actually happens]

Please:
1. Identify the root cause
2. Explain why this is happening
3. Provide a fix with explanation
4. Suggest how to prevent similar issues
5. Recommend debugging techniques for future
```

### Performance Issue

```
My application has performance issues:

**Problem**: [Slow page load / High memory / etc.]

**Metrics**:
- Current performance: [response time, memory usage, etc.]
- Target performance: [goals]
- Scale: [users, requests, data size]

**Profiling Data**:
```
[Performance profiling output]
```

**Code Sections**:
```[language]
[Suspected slow code]
```

**Questions**:
1. What's causing the bottleneck?
2. How can I optimize this?
3. What's the expected improvement?
4. Are there architectural changes needed?
5. What monitoring should I add?
```

---

## Architecture and Design

### System Design

```
Design a [system type] that [main purpose].

**Requirements**:
- Scale: [expected users/load]
- Availability: [uptime requirements]
- Latency: [response time requirements]
- Consistency: [data consistency needs]

**Constraints**:
- Budget: [cloud costs, infrastructure]
- Team size: [developers available]
- Timeline: [delivery expectations]
- Existing systems: [what to integrate with]

**Functional Requirements**:
1. [Feature 1]
2. [Feature 2]
3. [Feature 3]

**Non-Functional Requirements**:
- Security: [requirements]
- Compliance: [regulations]
- Maintainability: [team expertise]

Please provide:
1. High-level architecture diagram (text-based)
2. Technology stack recommendations with rationale
3. Database design approach
4. API design
5. Scalability strategy
6. Security measures
7. Monitoring and observability plan
8. Trade-offs and alternatives considered
```

### Microservices Architecture

```
Design a microservices architecture for [application domain].

Current State:
- [Monolith description or starting point]

Goals:
- [Goal 1: e.g., independent deployment]
- [Goal 2: e.g., better scalability]
- [Goal 3: e.g., team autonomy]

Please provide:
1. Service boundaries (what services and why)
2. Communication patterns (sync/async, protocols)
3. Data management strategy (DB per service, shared data)
4. Service discovery approach
5. API Gateway design
6. Authentication/Authorization across services
7. Monitoring and tracing strategy
8. Migration plan from current state
9. Potential pitfalls and how to avoid them
```

---

## Testing

### Unit Test Generation

```
Generate comprehensive unit tests for this code:

```[language]
[Your code]
```

Testing Framework: [Jest/Pytest/JUnit/etc.]

Requirements:
- Test all functions/methods
- Cover edge cases and error conditions
- Include positive and negative test cases
- Mock external dependencies
- Aim for >90% code coverage
- Include setup and teardown if needed
- Use descriptive test names
- Add comments for complex test logic

For each test:
- Arrange: Setup test data
- Act: Execute the function
- Assert: Verify the results
```

### Integration Test Plan

```
Create an integration test plan for [feature/system].

System Components:
- [Component 1: API]
- [Component 2: Database]
- [Component 3: External service]

Workflows to Test:
1. [Workflow 1 description]
2. [Workflow 2 description]

Provide:
1. Test scenarios with steps
2. Expected outcomes
3. Test data requirements
4. Environment setup
5. Test implementation code
6. Assertions to verify
7. Error scenarios to test
8. Performance benchmarks
```

---

## Documentation

### API Documentation

```
Create comprehensive API documentation for these endpoints:

[Provide API code or specifications]

Include:
1. Overview and purpose
2. Authentication method
3. Base URL and versioning
4. For each endpoint:
   - Method and path
   - Description
   - Parameters (path, query, body)
   - Request example with curl
   - Response examples (success and errors)
   - HTTP status codes
   - Rate limits
5. Error handling format
6. Code examples in [languages you want]
7. Common use cases
8. Best practices for API consumers

Format: [OpenAPI/Swagger or Markdown]
```

### Technical Documentation

```
Create technical documentation for [component/system].

Audience: [New developers/DevOps/End users]

Include:
1. Overview and purpose
2. Architecture diagram (text-based or Mermaid)
3. Setup and installation
4. Configuration options
5. Usage examples
6. API reference if applicable
7. Troubleshooting guide
8. FAQs
9. Contributing guidelines
10. Changelog

Style: Clear, concise, with plenty of examples
Format: Markdown
```

---

## Refactoring

### Code Refactoring

```
Refactor this code for better [maintainability/performance/readability]:

```[language]
[Code to refactor]
```

Current Issues:
- [Issue 1]
- [Issue 2]

Goals:
- [Goal 1: e.g., reduce complexity]
- [Goal 2: e.g., improve testability]

Constraints:
- Must maintain backward compatibility: [Yes/No]
- Must preserve current functionality: [Yes]
- Cannot change: [specific aspects]

Please:
1. Identify code smells
2. Propose refactoring strategy
3. Show refactored code
4. Explain improvements
5. Show before/after metrics (complexity, etc.)
6. Provide migration guide if needed
```

### Design Pattern Application

```
Apply appropriate design patterns to improve this code:

```[language]
[Your code]
```

Problems with current design:
- [Problem 1]
- [Problem 2]

Provide:
1. Which design patterns would help and why
2. Refactored code using these patterns
3. Class/component diagrams (text-based)
4. Explanation of how patterns solve the problems
5. Trade-offs of this approach
6. Alternative patterns considered

Patterns to consider: [list if you have preferences]
```

---

## Performance Optimization

### Optimization Audit

```
Optimize this code for performance:

```[language]
[Code to optimize]
```

Current Performance:
- [Metric 1: e.g., 500ms response time]
- [Metric 2: e.g., 200MB memory usage]

Target Performance:
- [Goal 1: e.g., <100ms response time]
- [Goal 2: e.g., <50MB memory usage]

Constraints:
- [Any limitations]

Please analyze:
1. Current bottlenecks
2. Time complexity analysis
3. Space complexity analysis
4. Optimization opportunities
5. Optimized code with explanations
6. Expected performance improvements
7. Trade-offs made
8. Benchmarking approach
```

### Database Query Optimization

```
Optimize these database queries:

Database: [PostgreSQL/MySQL/MongoDB/etc.]

Current Queries:
```sql
[Your queries]
```

Performance Issues:
- Query 1: [time taken, problem]
- Query 2: [time taken, problem]

Schema:
```sql
[Relevant table schemas]
```

Data Scale:
- [Table sizes, growth rate]

Please provide:
1. Explain why current queries are slow
2. Optimized queries
3. Index recommendations
4. Query execution plans
5. Alternative approaches (caching, denormalization)
6. Expected improvement
7. Monitoring queries to track performance
```

---

## Additional Prompts

### Git Commit Messages

```
Generate a conventional commit message for these changes:

Changes:
[Summary of what changed]

Files modified:
- [file1]
- [file2]

Format: [Conventional Commits]
Type: [feat/fix/docs/refactor/test/chore]

Include:
- Short summary (<50 chars)
- Detailed description if needed
- Breaking changes if any
- Issue references if applicable
```

### Code Translation

```
Translate this code from [Source Language] to [Target Language]:

```[source]
[Original code]
```

Requirements:
- Use idiomatic [target language] patterns
- Maintain equivalent functionality
- Follow [target language] best practices
- Include type hints/annotations
- Add comments for language-specific differences
- Suggest library equivalents
- Note any behavioral differences
```

---

## Quick Tips

1. **Be Specific**: Mention your tech stack, versions, and constraints
2. **Provide Context**: Explain why you need something, not just what
3. **Include Examples**: Show current code or desired output
4. **Set Standards**: Mention style guides, patterns, or conventions to follow
5. **Ask for Explanations**: Don't just get code, understand it
6. **Iterate**: Start simple, then refine based on the output

---

**See Also**:
- [AI Best Practices](../../AI-BEST-PRACTICES.md)
- [Developer's Quick Start Guide](../../guides/developers.md)
- [Testing Strategies](./testing-strategies.md)

**Last Updated**: 2025-10-28
