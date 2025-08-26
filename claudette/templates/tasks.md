# Implementation Tasks: [FEATURE NAME]

**Project**: [Feature ID] - [Feature Name]
**Estimated Duration**: [X days/weeks based on user approval]
**Engineer Assigned**: TBD  
**Context7 Validated**: [DATE] - [Technologies/versions confirmed]
**Lead Architect Consulted**: [DATE] - [Technical proposals and refinements completed]
**Status**: Not Started | In Progress | Review | Complete

## About This Document

This tasks document contains comprehensive implementation guidance created through collaboration between the lead architect and user during feature planning. Each task includes:

- **Architect's Implementation Guide**: Step-by-step technical instructions
- **Code Examples**: Concrete implementation patterns to follow
- **Testing Requirements**: Specific test scenarios and coverage targets
- **Acceptance Criteria**: Measurable success conditions
- **Technical Notes**: Decisions and alternatives discussed during planning

**For Engineers**: Follow the architect's implementation guide exactly. If guidance is unclear or missing, consult with the lead architect before proceeding.

**For Reviewers**: Verify implementation matches the architect's specified patterns and meets all acceptance criteria.

---

## Required Technology Versions

**CRITICAL**: Use ONLY these exact versions as specified in feature.md Technology Stack table. These were validated during Context7 consultation and user approval.

### Installation Requirements
```bash
# Copy exact commands from feature.md Technology Stack section
[package-manager] install [library]@[version]
[package-manager] install [framework]@[version]
# ... (all packages with exact versions)
```

**Version Verification**: Before starting implementation, verify current versions match feature.md specifications:
```bash
[package-manager] list --depth=0 | grep [package-name]
```

**If versions differ from feature.md**: STOP implementation and update packages to match approved versions.

---

## Overview & Success Criteria

### Definition of Done
- [ ] All acceptance criteria from feature.md validated
- [ ] **QA validation passed** for all waves and final feature validation
- [ ] Code review completed with team lead approval  
- [ ] Unit test coverage ≥ 85% (measured by [tool])
- [ ] Integration tests covering all API endpoints
- [ ] **E2E tests passing** for feature scenarios
- [ ] **Build verification** for all affected applications
- [ ] **Dev servers start** successfully
- [ ] Security scan passed with no high/critical issues
- [ ] Performance benchmarks met: [specific metrics]
- [ ] Documentation updated (README, API docs, inline comments)
- [ ] Deployed to staging and validated
- [ ] Production deployment successful

### QA Validation Process
This feature uses wave-based QA validation to ensure quality:

**Wave Validation** (After completing each wave):
- QA agent discovers and runs appropriate test suites for the wave
- Tests include: unit tests, integration tests, lint, typecheck, build
- Must pass QA validation before proceeding to next wave
- Feedback loop with engineer if issues found

**Final Feature Validation** (After all waves complete):
- QA agent runs comprehensive validation for entire feature
- Includes: full test suite, E2E tests, build verification, dev server startup
- Validates all acceptance criteria from feature.md
- Must pass final QA before feature marked complete

**Validation Requirements**:
- Each task must include its own tests (TDD approach)
- Wave-level validation ensures no regressions between tasks
- Final validation ensures complete feature works end-to-end
- QA agent discovers test commands from project structure (stack-agnostic)

### Key Success Metrics
- **Performance**: [specific response time/throughput targets]
- **Reliability**: [uptime/error rate targets]  
- **Security**: [security requirements compliance]
- **Quality**: [test coverage, code review standards]

---

## Phase 1: Foundation & Database Layer
**Estimated Duration**: [X days]
**Dependencies**: [Any prerequisite tasks or external dependencies]

### Database Schema & Models
- [ ] **Design [Model1] schema** with fields: [specific fields]
  
  **Architect's Implementation Guide**:
  - Step 1: Create migration file using approved [ORM] v[X.Y.Z] migration patterns
  - Step 2: Define schema with proper data types and constraints
  - Step 3: Add performance indexes based on anticipated query patterns
  - Step 4: Include audit fields (created_at, updated_at, deleted_at)
  - Architecture pattern: [Repository Pattern with Active Record/Data Mapper]
  
  **Code Example**:
  ```sql
  -- Migration template provided by architect
  CREATE TABLE [table_name] (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    [field1] VARCHAR(255) NOT NULL,
    [field2] INTEGER DEFAULT 0,
    created_at TIMESTAMP DEFAULT NOW(),
    updated_at TIMESTAMP DEFAULT NOW(),
    deleted_at TIMESTAMP NULL,
    -- Constraints from architect's design
    CONSTRAINT unique_[field1] UNIQUE ([field1]),
    CONSTRAINT check_[field2] CHECK ([field2] >= 0)
  );
  
  -- Performance indexes recommended by architect
  CREATE INDEX idx_[table]_[field] ON [table_name] ([field1]);
  CREATE INDEX idx_[table]_active ON [table_name] (deleted_at) WHERE deleted_at IS NULL;
  ```
  
  **Testing Requirements**:
  - Unit test scenarios: Schema creation, constraint validation, index performance
  - Integration test: Migration up/down, seed data loading
  - Coverage target: 100% for schema definition
  
  **Acceptance Criteria**:
  - [ ] Schema matches architect's approved design exactly
  - [ ] All constraints prevent invalid data as specified
  - [ ] Indexes improve query performance by [X]% on test dataset
  - [ ] Migration runs cleanly in all environments
  
  **Technical Notes from Planning**:
  - [Any special considerations discussed with user during refinement]
  - [Performance requirements validated with architect]
  - [Alternative approaches considered and why rejected]
  
  **QA Validation**:
  - Task tests must pass before commit
  - Wave-level QA validation will verify this task with others in the wave
  - Final feature QA will ensure this task works in complete feature context
  
  **Estimated Time**: [X hours]

- [ ] **Design [Model2] schema** with relationships to [Model1]
  - Define foreign key relationships and cascading rules
  - Add composite indexes for query optimization
  - **Estimated Time**: [X hours]

- [ ] **Create database migration scripts**
  - Forward migration with schema creation
  - Rollback migration for safe reversion
  - Include seed data for testing
  - **Estimated Time**: [X hours]

### Repository Layer Implementation
- [ ] **Implement [Model1]Repository** with methods:
  - `create(data)` - Insert with validation
  - `findById(id)` - Retrieve with error handling
  - `findByEmail(email)` - Custom query method
  - `update(id, data)` - Partial updates only
  - `softDelete(id)` - Mark as deleted, don't remove
  - **Estimated Time**: [X hours]

- [ ] **Create repository unit tests** (Target: 90% coverage)
  - Test all CRUD operations with valid/invalid data
  - Test edge cases: non-existent IDs, duplicate keys
  - Mock database layer for isolated testing
  - **Estimated Time**: [X hours]

- [ ] **Create repository integration tests**
  - Test with real database (test schema)
  - Test transaction rollback scenarios
  - Test concurrent access patterns
  - **Estimated Time**: [X hours]

### Environment & Configuration Setup
- [ ] **Install exact technology stack versions**
  - Execute installation commands from feature.md Technology Stack table
  - Verify installed versions match specifications exactly
  - Document any version conflicts and resolution steps
  - **Estimated Time**: [X hours]

- [ ] **Set up development environment**
  - Create `.env.example` with all required variables
  - Update `README.md` with setup instructions and version requirements
  - Configure database connection pooling using approved [Database] v[X.Y.Z]
  - **Estimated Time**: [X hours]

- [ ] **Add environment-specific configs**
  - Development, staging, production configs using [Framework] v[X.Y.Z] patterns
  - Database connection strings for [Database] v[X.Y.Z]
  - Configuration management using approved libraries only
  - **Estimated Time**: [X hours]

---

## Phase 2: Business Logic & Service Layer  
**Estimated Duration**: [X days]
**Dependencies**: Phase 1 complete

### Core Service Implementation
- [ ] **Implement [Service1]** with methods:
  
  **Architect's Implementation Guide**:
  - Step 1: Create service class following [Dependency Injection pattern]
  - Step 2: Implement constructor with repository dependencies
  - Step 3: Add business logic methods with input validation
  - Step 4: Implement comprehensive error handling with custom exceptions
  - Step 5: Add structured logging for debugging and monitoring
  - Architecture pattern: [Service Layer with Repository injection]
  
  **Code Example**:
  ```javascript
  // Service template provided by architect
  class [Service1] {
    constructor([repository1], [repository2], logger) {
      this.[repository1] = [repository1];
      this.[repository2] = [repository2];
      this.logger = logger;
    }
    
    async [method1](params) {
      try {
        // Architect's validation pattern
        this.validateInput(params);
        
        // Business logic implementation
        const result = await this.[repository1].create(params);
        
        // Logging pattern from architect
        this.logger.info('[Service1].[method1] completed', { 
          id: result.id, 
          duration: performance.now() - startTime 
        });
        
        return result;
      } catch (error) {
        // Error handling pattern from architect
        this.logger.error('[Service1].[method1] failed', { 
          params, 
          error: error.message 
        });
        throw new [CustomException]('Failed to [business operation]', error);
      }
    }
    
    private validateInput(params) {
      // Validation logic as specified by architect
      if (!params.[required_field]) {
        throw new ValidationError('[required_field] is required');
      }
    }
  }
  ```
  
  **Testing Requirements**:
  - Unit test scenarios: All method paths, validation errors, business logic edge cases
  - Mock dependencies: Repository calls, external services
  - Coverage target: 85% minimum, 95% preferred
  - Test patterns: AAA (Arrange, Act, Assert), Given-When-Then
  
  **Acceptance Criteria**:
  - [ ] All business methods implement architect's error handling pattern
  - [ ] Input validation prevents invalid business operations
  - [ ] Logging provides sufficient debugging information
  - [ ] Service integrates cleanly with repository layer
  - [ ] Custom exceptions provide clear error messages for UI
  
  **Technical Notes from Planning**:
  - [Specific business rules validated during user discussions]
  - [Performance requirements: method should complete in <[X]ms]
  - [Integration points with external services discussed]
  
  **Alternative Approaches Considered**:
  - [Alternative pattern rejected during planning and why]
  
  **Estimated Time**: [X hours]

- [ ] **Implement [Service2]** handling:
  - [Specific business responsibility 1]
  - [Specific business responsibility 2]  
  - Integration with external service: [service name]
  - Fallback strategy if external service fails
  - **Estimated Time**: [X hours]

### Domain Logic & Business Rules
- [ ] **Implement business rule**: [Specific rule description]
  - Add validation logic with clear error messages
  - Create custom exceptions for business rule violations
  - **Estimated Time**: [X hours]

- [ ] **Add domain events** for:
  - [Event 1]: [when it's triggered and what data it carries]
  - [Event 2]: [trigger conditions and payload]
  - Implement event publisher with async handling
  - **Estimated Time**: [X hours]

### Security & Validation Layer
- [ ] **Implement input validation** for all service methods
  - Use schema validation library: [specific library]
  - Sanitize inputs to prevent injection attacks
  - Add comprehensive input testing (boundary values, malformed data)
  - **Estimated Time**: [X hours]

- [ ] **Add authentication service** with:
  - JWT token generation with proper expiration
  - Token refresh mechanism with rotation
  - Rate limiting for auth attempts (max [X] per minute)
  - **Estimated Time**: [X hours]

### Service Layer Testing
- [ ] **Create service unit tests** (Target: 85% coverage)
  - Test all business logic paths with mocked dependencies
  - Test error scenarios and exception handling
  - Test edge cases and boundary conditions
  - **Estimated Time**: [X hours]

- [ ] **Add integration tests** for service layer
  - Test services with real repository layer
  - Test external service integration with mocked endpoints
  - Test transaction boundaries and rollback scenarios
  - **Estimated Time**: [X hours]

---

## Phase 3: API Layer & Endpoints
**Estimated Duration**: [X days]  
**Dependencies**: Phase 2 complete

### REST API Implementation
- [ ] **Implement `POST /api/v1/[resource]`** endpoint
  
  **Architect's Implementation Guide**:
  - Step 1: Create route handler using approved [Framework] v[X.Y.Z] patterns
  - Step 2: Add request validation middleware with JSON schema
  - Step 3: Implement authentication and authorization checks
  - Step 4: Add rate limiting and request logging
  - Step 5: Call service layer and handle business logic errors
  - Step 6: Format response according to API specification
  - Architecture pattern: [Controller → Service → Repository pattern]
  
  **Code Example**:
  ```javascript
  // API endpoint template provided by architect
  app.post('/api/v1/[resource]', [
    // Middleware stack from architect
    authenticationMiddleware,
    rateLimitMiddleware({ max: [X] }),
    validationMiddleware([resourceSchema]),
    authorizationMiddleware(['create:[resource]'])
  ], async (req, res, next) => {
    try {
      const startTime = performance.now();
      
      // Service call as specified by architect
      const result = await [service].create(req.body, {
        userId: req.user.id,
        correlationId: req.correlationId
      });
      
      // Response format from architect's API specification
      const response = {
        id: result.id,
        ...result.toPublicJSON(),
        createdAt: result.createdAt,
        _links: {
          self: { href: `/api/v1/[resource]/${result.id}` }
        }
      };
      
      // Logging pattern from architect
      req.logger.info('POST /api/v1/[resource] completed', {
        resourceId: result.id,
        duration: performance.now() - startTime
      });
      
      res.status(201).json(response);
    } catch (error) {
      // Error handling pattern from architect
      if (error instanceof ValidationError) {
        return res.status(400).json({
          error: 'Validation failed',
          details: error.details
        });
      }
      
      if (error instanceof BusinessLogicError) {
        return res.status(409).json({
          error: error.message,
          code: error.code
        });
      }
      
      // Unhandled errors
      next(error);
    }
  });
  ```
  
  **Testing Requirements**:
  - Unit tests: Happy path, validation errors, auth failures, business logic errors
  - Integration tests: Full request/response cycle with real database
  - Security tests: Authentication bypass, authorization escalation, rate limiting
  - Performance tests: Response time under load
  - Coverage target: 90% for endpoint logic
  
  **Acceptance Criteria**:
  - [ ] Endpoint validates input according to architect's schema
  - [ ] Authentication and authorization work as specified
  - [ ] Rate limiting prevents abuse as configured
  - [ ] Response format matches API specification exactly
  - [ ] Error responses provide clear, actionable messages
  - [ ] Endpoint handles all error scenarios gracefully
  
  **Technical Notes from Planning**:
  - [Rate limiting discussed: [X] requests per minute for this endpoint]
  - [Response format refined during user review]
  - [Specific validation rules confirmed with user]
  
  **Alternative Approaches Considered**:
  - [GraphQL vs REST - REST chosen for simplicity during planning]
  
  **Estimated Time**: [X hours]

- [ ] **Implement `GET /api/v1/[resource]/:id`** endpoint
  - Parameter validation (UUID format for ID)
  - Authorization check (user can access this resource)
  - Handle not found scenarios gracefully
  - Include related data as specified: [related entities]
  - **Estimated Time**: [X hours]

- [ ] **Implement `PUT /api/v1/[resource]/:id`** endpoint
  - Partial update support (only update provided fields)
  - Optimistic locking to prevent concurrent modification issues
  - Permission checks for field-level updates
  - **Estimated Time**: [X hours]

- [ ] **Implement `DELETE /api/v1/[resource]/:id`** endpoint
  - Soft delete implementation (mark as deleted, don't remove)
  - Check for dependencies before allowing deletion
  - Audit log the deletion with user information
  - **Estimated Time**: [X hours]

### Middleware & Cross-cutting Concerns  
- [ ] **Add authentication middleware**
  - JWT token validation with proper error handling
  - Support for both header and cookie-based tokens
  - Handle expired tokens gracefully
  - **Estimated Time**: [X hours]

- [ ] **Implement authorization middleware**
  - Role-based access control for different user types
  - Resource-level permissions (users can only access their own data)
  - **Estimated Time**: [X hours]

- [ ] **Add rate limiting middleware**
  - Different limits for different endpoints: [specify limits]
  - IP-based and user-based rate limiting
  - Graceful degradation when limits exceeded
  - **Estimated Time**: [X hours]

- [ ] **Implement request logging middleware**
  - Log all API requests with correlation IDs
  - Include user information (anonymized if needed)
  - Performance timing for slow request detection
  - **Estimated Time**: [X hours]

### API Security & Validation
- [ ] **Add comprehensive input validation**
  - JSON schema validation for all POST/PUT requests
  - SQL injection prevention (parameterized queries only)
  - XSS prevention (output encoding)
  - **Estimated Time**: [X hours]

- [ ] **Implement API security headers**
  - CORS configuration for allowed origins
  - Security headers: CSP, HSTS, X-Frame-Options
  - API versioning strategy
  - **Estimated Time**: [X hours]

### API Testing
- [ ] **Create API integration tests** for all endpoints
  - Test happy path scenarios with valid data
  - Test error scenarios: validation errors, not found, unauthorized
  - Test rate limiting behavior
  - Test authentication and authorization
  - **Estimated Time**: [X hours]

- [ ] **Add API contract tests**
  - Ensure request/response format matches specification
  - Test with different content types and edge cases
  - **Estimated Time**: [X hours]

---

## Phase 4: Comprehensive Testing & Quality Assurance
**Estimated Duration**: [X days]
**Dependencies**: Phase 3 complete

### Unit Testing  
- [ ] **Achieve 85% unit test coverage** across all components
  - Repository layer: [current coverage]%
  - Service layer: [current coverage]%
  - API layer: [current coverage]%
  - Use coverage tool: [specific tool] for measurement
  - **Estimated Time**: [X hours]

- [ ] **Add edge case and error scenario tests**
  - Test boundary conditions (empty strings, null values, large inputs)
  - Test concurrent access scenarios
  - Test database connection failures and recovery
  - **Estimated Time**: [X hours]

### Integration Testing
- [ ] **Create full API integration test suite**
  - Test complete user workflows from registration to resource access
  - Test API endpoint interactions and data consistency
  - Test external service integration with real services (staging environment)
  - **Estimated Time**: [X hours]

- [ ] **Add database integration tests**
  - Test with real database using test fixtures
  - Test transaction rollback scenarios
  - Test database constraints and cascading deletes
  - **Estimated Time**: [X hours]

### End-to-End Testing
- [ ] **Create E2E tests for critical user journeys**
  - User registration → login → resource creation → retrieval flow
  - Error handling: invalid login, expired tokens, permission errors
  - Test with realistic data volumes
  - **Estimated Time**: [X hours]

### Performance Testing
- [ ] **Load test API endpoints** with target metrics:
  - Concurrent users: [X] users
  - Response time: [Y]ms for 95th percentile
  - Throughput: [Z] requests per second
  - Use tool: [specific load testing tool]
  - **Estimated Time**: [X hours]

- [ ] **Database performance testing**
  - Test query performance with realistic data volumes
  - Identify and optimize slow queries
  - Test connection pool under load
  - **Estimated Time**: [X hours]

### Security Testing
- [ ] **Run security vulnerability scans**
  - OWASP ZAP scan for common web vulnerabilities
  - Dependency vulnerability check using [tool]
  - SQL injection testing on all endpoints
  - **Estimated Time**: [X hours]

- [ ] **Manual security testing**
  - Authentication bypass attempts
  - Authorization escalation testing
  - Input validation testing with malicious payloads
  - **Estimated Time**: [X hours]

---

## Phase 5: Documentation & Deployment
**Estimated Duration**: [X days]  
**Dependencies**: Phase 4 complete

### Documentation  
- [ ] **Update API documentation** 
  - Complete OpenAPI/Swagger specification
  - Include request/response examples for all endpoints
  - Error code documentation with troubleshooting guides
  - **Estimated Time**: [X hours]

- [ ] **Update README.md** with:
  - Feature overview and business purpose
  - Setup and installation instructions
  - Environment variable configuration
  - Running tests and development workflow
  - **Estimated Time**: [X hours]

- [ ] **Add inline code documentation**
  - JSDoc/similar for all public methods
  - Complex business logic explanation
  - Architecture decision records for major choices
  - **Estimated Time**: [X hours]

### Deployment Preparation
- [ ] **Configure CI/CD pipeline**
  - Automated testing on pull requests
  - Security scanning integration
  - Automated deployment to staging
  - **Estimated Time**: [X hours]

- [ ] **Set up monitoring and alerting**
  - Application performance monitoring (APM)
  - Error rate and response time alerts
  - Database performance monitoring
  - **Estimated Time**: [X hours]

- [ ] **Create deployment runbook**
  - Step-by-step deployment process
  - Rollback procedures if deployment fails
  - Database migration execution plan
  - **Estimated Time**: [X hours]

### Production Deployment
- [ ] **Deploy to staging environment**
  - Run full test suite in staging
  - Performance testing with production-like data
  - User acceptance testing with stakeholders
  - **Estimated Time**: [X hours]

- [ ] **Production deployment**
  - Execute deployment during maintenance window
  - Run database migrations safely
  - Verify all endpoints are functioning
  - Monitor for errors and performance issues
  - **Estimated Time**: [X hours]

- [ ] **Post-deployment validation**
  - Smoke test all critical functionality
  - Monitor error rates and performance metrics
  - Validate with real user scenarios
  - **Estimated Time**: [X hours]

---

## Risk Mitigation & Contingency Plans

### High-Risk Tasks
1. **Database Migration in Production**
   - **Risk**: Data corruption or extended downtime
   - **Mitigation**: Test migration multiple times in staging with production data copy
   - **Contingency**: Have rollback scripts ready and database backup verified

2. **External Service Integration** 
   - **Risk**: [External service] may be unreliable
   - **Mitigation**: Implement circuit breaker pattern and fallback mechanisms
   - **Contingency**: Graceful degradation of functionality if service unavailable

### Technical Debt Items
1. **[Specific technical shortcut taken]** - Address in next sprint
2. **[Performance optimization deferred]** - Monitor and optimize based on usage patterns

---

## Progress Tracking

### Completion Status
**Phase 1**: ⬜ Not Started | 🟡 In Progress | ✅ Complete  
**Phase 2**: ⬜ Not Started | 🟡 In Progress | ✅ Complete  
**Phase 3**: ⬜ Not Started | 🟡 In Progress | ✅ Complete  
**Phase 4**: ⬜ Not Started | 🟡 In Progress | ✅ Complete  
**Phase 5**: ⬜ Not Started | 🟡 In Progress | ✅ Complete  

### Time Tracking
- **Estimated Total**: [X] hours
- **Actual Time**: [Y] hours  
- **Variance**: [Z] hours ([+/-]%)

### Blockers & Decisions Log
**[DATE]** - [Decision/Blocker]: [Description and resolution]
**[DATE]** - [Decision/Blocker]: [Description and resolution]

---

## Notes & Learnings
[Track important decisions, architectural insights, and lessons learned during implementation]