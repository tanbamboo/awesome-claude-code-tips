# Complete Git & GitHub Workflow Example

## Scenario: Adding User Authentication Feature

*For more detailed guidance on Claude Code best practices, see [README.md](README.md)*

### Step 1: Start New Feature

**You:** "Let's add user authentication to our app"

**Me:** "First, let's check current state and create a feature branch"

```bash
# Check current state
git status
git branch

# Create feature branch
git checkout -b feature/user-authentication
```

### Step 2: Work on Feature

**You:** "Help me implement [JWT authentication](https://jwt.io/introduction)"

**Me:** [Code implementation work - creating auth service, middleware, etc.]

**During development:**
```
# Check what I've changed
git diff

# Commit logical chunks of work
git add .
git commit -m "feat: add JWT authentication service with token generation" # See [Conventional Commits](https://www.conventionalcommits.org/)
```

### Step 3: Complete Feature

**Me:** "Let's review what we've built and commit the final changes"

```bash
# See all changes
git status
git diff --staged

# Commit remaining work
git add .
git commit -m "feat: implement authentication middleware and protected routes

- Add [JWT middleware](https://www.npmjs.com/package/express-jwt) for route protection
- Implement /login and /register endpoints
- Add user model and database schema
- Include authentication tests
- Update API documentation"
```

### Step 4: Prepare for Pull Request

**You:** "Ready to create a PR"

**Me:** "Let me check your branch and draft a PR description"

```bash
# Check branch status
git status
git log --oneline -5

# Push your branch
git push -u origin feature/user-authentication
```

**Me:** "Here's your PR description:

## Summary
Add JWT-based user authentication system with secure token handling and protected routes.

## Changes Made
- ✅ JWT authentication service with token generation/validation
- ✅ Authentication middleware for route protection
- ✅ User registration and login endpoints
- ✅ User model and database schema
- ✅ Comprehensive unit tests (95% coverage)
- ✅ Updated API documentation

## Test Plan
- [ ] User registration with valid/invalid data
- [ ] User login with correct/incorrect credentials
- [ ] Token validation and expiration handling
- [ ] Protected route access control
- [ ] Error handling for edge cases
- [ ] Integration testing with frontend

## Checklist
- [ ] Code follows project conventions
- [ ] All tests pass
- [ ] No security vulnerabilities
- [ ] Documentation updated
- [ ] Ready for review

Run this command:
```bash
gh pr create --title 'feat: add JWT authentication system' --body '[PR description above]' # See [GitHub CLI PR docs](https://cli.github.com/manual/gh_pr_create)
```

### Step 5: Handle PR Review

**Reviewer:** "Can you add [rate limiting](https://www.npmjs.com/package/express-rate-limit) to the auth endpoints?"

**Me:** "Let's add rate limiting and commit the changes"

```bash
# Make the changes
git add .
git commit -m "feat: add rate limiting to authentication endpoints

- Implement IP-based rate limiting
- Add rate limit headers to responses
- Update tests to cover rate limiting scenarios"

# Update the PR
git push origin feature/user-authentication
```

### Step 6: Address Review Comments

**Me:** "Let me respond to the review comments:

> **Rate Limiting Added** ✅
> - Added IP-based rate limiting (100 requests per 15 minutes)
> - Includes rate limit headers in responses
> - Comprehensive test coverage for rate limiting scenarios
> 
> Ready for another review!"

### Step 7: Merge and Cleanup

**You:** "PR is approved, let's merge it"

**Me:** "Here's the merge workflow:

```bash
# Switch to main branch
git checkout main

# Pull latest changes
git pull origin main

# Merge the feature branch
git merge feature/user-authentication

# Push to remote
git push origin main

# Delete the feature branch
git branch -d feature/user-authentication
git push origin --delete feature/user-authentication
```

### Step 8: Create Follow-up Issue

**Me:** "Let's create a follow-up issue for the next phase:

**Issue: Add Social Login (OAuth) Integration**

## Description
Extend authentication system to support social login providers (Google, GitHub, etc.)

## Acceptance Criteria
- [ ] Google OAuth integration - see [Google OAuth docs](https://developers.google.com/identity/protocols/oauth2)
- [ ] GitHub OAuth integration - see [GitHub OAuth docs](https://docs.github.com/en/apps/oauth-apps/building-oauth-apps/creating-an-oauth-app)  
- [ ] User profile linking
- [ ] Social login UI components
- [ ] Error handling for failed social logins
- [ ] Documentation updates

## Labels
`enhancement`, `authentication`, `frontend`

## Milestone
`v2.0 - User Management`

Run this command:
```bash
gh issue create --title "feat: add social login (OAuth) integration" --body "[Issue description above]" # See [GitHub CLI issue docs](https://cli.github.com/manual/gh_issue_create)
```

## Key Principles Demonstrated

1. **You control git operations** - I suggest, you execute
2. **I write good commit messages** - You review and run them
3. **Small, logical commits** - Each has a clear purpose
4. **Comprehensive PR descriptions** - Clear context for reviewers
5. **Respond to feedback** - Address review comments professionally
6. **Clean branch management** - Delete branches after merging
7. **Plan next work** - Create issues for future improvements

## Anti-Patterns Avoided

❌ **No giant commits** - Each commit has a focused purpose
❌ **No working on main** - Always use feature branches
❌ **No vague PR descriptions** - Clear context and testing checklist
❌ **No unresponsive to reviews** - Address feedback promptly
❌ **No abandoned branches** - Clean up after merging