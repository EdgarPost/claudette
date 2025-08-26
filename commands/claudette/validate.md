---
name: validate
description: Validate that features work correctly and meet acceptance criteria
model: sonnet
---

You validate that implemented features are working correctly and meeting their acceptance criteria.

Make sure to read the ~/.claude/claudette/commands-subagents-guide.md for file structure and general guidelines.

## Purpose

Allow users to verify that features (existing or just implemented) are functioning properly and meeting their acceptance criteria through comprehensive QA validation.

## Usage Modes

### 1. Validate Active Feature
```bash
/claudette-validate
```
Validates the currently active feature from STATUS.md

### 2. Validate Specific Feature  
```bash
/claudette-validate [feature-id]
```
Validates a specific feature by ID (e.g., 0003-auth)

### 3. Validate All Features (Regression Suite)
```bash
/claudette-validate all
```
Runs validation for all implemented features

## Process

### Step 1: Determine Validation Scope
- **No argument**: Read root STATUS.md to get active feature
- **Feature ID provided**: Validate specific feature by ID
- **"all" provided**: Discover all features in planning/features/

### Step 2: Load Feature Context
For each feature to validate:
1. **Read feature.md** for acceptance criteria and technical details
2. **Read tasks.md** to understand implementation scope
3. **Read feature's STATUS.md** for current state
4. **Check feature's ACTIVITY.md** for recent changes

### Step 3: Delegate to QA Agent
1. **Delegate to claudette-qa** in Feature Validation mode
2. **Provide feature context** (acceptance criteria, scope, etc.)
3. **Await comprehensive validation results**
4. **Handle feedback loop** if issues found

### Step 4: Process and Report Results
1. **Log validation results** to feature's ACTIVITY.md
2. **Update feature's STATUS.md** if validation changes status
3. **Provide user with clear next steps**

## Response Examples

### Single Feature Validation (Success)
```
Human: /claudette-validate

Claudette: Starting validation for active feature "User Authentication"...

*Delegates to claudette-qa*

✅ Feature "User Authentication" Validation Complete
✓ All unit tests passing (47 tests)
✓ Integration tests passing (12 scenarios)  
✓ E2E tests passing (5 user journeys)
✓ All acceptance criteria verified
✓ Build successful
✓ Dev server starts correctly

🎯 Feature is working perfectly and ready for production.
```

### Single Feature Validation (Issues Found)
```
Human: /claudette-validate 0003-auth

Claudette: Validating feature 0003-auth "User Authentication"...

*Delegates to claudette-qa*

⚠️ Feature "User Authentication" Has Issues:

❌ Failed Tests: 2 failures found
  • auth.test.js: JWT refresh token test failing
  • integration/login.test.js: Session persistence broken

❌ Acceptance Criteria Issues:
  • "Users can stay logged in across sessions" - Not met
  • "Refresh tokens expire after 7 days" - Test failing

📍 Likely Cause: Recent database schema changes affected token storage

💡 Recommendations:
  1. Fix JWT refresh token handling in AuthService
  2. Update session persistence logic for new schema
  3. Re-run validation after fixes: /claudette-validate 0003-auth

🔧 Feature needs attention before it can be considered working.
```

### All Features Validation (Regression Suite)
```
Human: /claudette-validate all

Claudette: Running comprehensive validation for all 5 implemented features...

*Validates each feature via claudette-qa*

📊 Validation Results Summary:

✅ Feature 0001-dashboard: All tests passing
✅ Feature 0002-user-mgmt: All tests passing
⚠️ Feature 0003-auth: 2 test failures (see details above)
✅ Feature 0004-api-docs: All tests passing  
✅ Feature 0005-notifications: All tests passing

📈 Overall Status: 4/5 features fully working
⚠️ 1 feature needs attention: User Authentication

🎯 Recommendation: Fix Feature 0003 issues before deployment
```

## Error Handling

### Feature Not Found
```
⚠️ Feature "0099-nonexistent" not found in planning/features/
Available features:
  • 0001-dashboard
  • 0002-user-mgmt  
  • 0003-auth
  • 0004-api-docs
  • 0005-notifications

Use: /claudette-validate [feature-id]
```

### No Active Feature
```
⚠️ No active feature found in STATUS.md
Either:
  • /claudette-validate [feature-id] - Validate specific feature
  • /claudette-validate all - Validate all features
  • /claudette-feature [name] - Create new feature first
```

### Validation Environment Issues
```
⚠️ Validation environment issues detected:
  • No test commands found in package.json
  • Build tools not available
  • Dev dependencies missing

💡 Recommendations:
  1. Ensure project dependencies are installed
  2. Check README.md for setup instructions
  3. Verify test scripts exist in package.json

Cannot proceed with validation until environment is ready.
```

## Integration with Other Commands

### After Implementation
```
Human: /claudette-implement
[Implementation completes]
Claudette: Feature implementation complete! 
Suggest: /claudette-validate - Verify everything works correctly
```

### Before Deployment
```
Human: Ready to deploy feature 0003-auth
Human: /claudette-validate 0003-auth
[Validation runs]
Claudette: ✅ Feature verified working - safe to deploy
```

### After Major Changes
```
Human: Just refactored the database layer
Human: /claudette-validate all
[Regression testing]
Claudette: 3/5 features affected, all still working ✅
```

## Performance Expectations

### Single Feature: < 15 minutes
- Comprehensive test suite
- Build verification
- E2E scenarios
- Acceptance criteria check

### Multiple Features: < 5 minutes per feature
- Parallel validation where possible
- Smart test selection
- Cached results for unchanged features

### Regression Suite (All): < 30 minutes
- Full validation of all features
- Complete regression testing
- Comprehensive reporting

## Logging and Tracking

### Feature Activity Log
Each validation logs to feature's ACTIVITY.md:
```
## [DATE] - QA Validation Run
**Trigger**: Manual validation via /claudette-validate
**Result**: ✅ All tests passing
**Duration**: 8m 23s
**Issues**: None found
**Next Action**: Feature ready for deployment
```

### Status Updates
Updates feature's STATUS.md if validation affects status:
- Working → Broken (if validation fails)
- Unknown → Verified (if validation passes)
- Complete → Needs Attention (if regressions found)

## Next Steps After Validation

Always suggest appropriate next actions based on results:

**If all pass:**
- Feature ready for deployment
- Consider running validation before major changes
- Use `/claudette-validate all` for regression testing

**If failures found:**
- Fix specific issues identified
- Re-run validation to confirm fixes
- Consider rolling back recent changes if needed
- Use `/claudette-implement` if major fixes required

**If environment issues:**
- Follow setup instructions in README
- Install missing dependencies
- Configure test environment properly