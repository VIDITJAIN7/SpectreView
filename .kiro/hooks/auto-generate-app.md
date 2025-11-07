# Hook: Auto-Generate App

## Description

The ULTIMATE automation hook! Fill ONLY the requirements file, save it, and get a complete working application. This master hook generates design.md and tasks.md from your requirements, then scaffolds and generates all code automatically.

## Trigger

**Event**: File Saved  
**File Pattern**: 
- `templates/requirements.md` (ONLY file you need to edit!)

## Workflow

This hook runs FOUR workflows in sequence:

### 1. Generate Design & Tasks from Requirements
- Reads and analyzes your requirements.md
- Extracts app name, description, user stories, acceptance criteria
- Infers data models from requirements
- **Generates templates/design.md** with complete architecture, data models, API design
- **Generates templates/tasks.md** with implementation task breakdown
- **If generation fails**: Stops and reports errors
- **If generation succeeds**: Proceeds to validation

### 2. Validate All Files
- Validates requirements.md has user stories
- Validates generated design.md has all sections
- Validates generated tasks.md has actionable steps
- **If validation fails**: Stops and reports errors
- **If validation passes**: Proceeds to scaffolding

### 3. Scaffold Application
- Creates complete directory structure
- Generates configuration files
- Creates entry points
- Sets up testing infrastructure
- **If scaffolding fails**: Stops and reports errors
- **If scaffolding succeeds**: Proceeds to boilerplate generation

### 4. Generate Boilerplate
- Analyzes data models from generated design.md
- Generates backend code (models, routes, services)
- Generates frontend code (components, hooks, stores)
- Creates utility code (validation, helpers)
- Adds documentation comments

## Context Files

**Input (User fills this):**
- `templates/requirements.md` - The ONLY file you need to customize!

**Auto-Generated (Hook creates these):**
- `templates/design.md` - Generated from requirements
- `templates/tasks.md` - Generated from requirements

**Reference (Used for generation):**
- `.kiro/steering/product.md`
- `.kiro/steering/structure.md`
- `.kiro/steering/tech.md`

## Expected Output

### Success Case

```
=== STEP 1: GENERATE DESIGN & TASKS ===
✓ Analyzed requirements.md (7 user stories, 35 acceptance criteria)
✓ Generated templates/design.md (8 sections, 3 data models)
✓ Generated templates/tasks.md (15 tasks, 45 sub-tasks)

=== STEP 2: VALIDATION ===
✓ Requirements: Complete with user stories
✓ Design: All sections filled, data models defined
✓ Tasks: Actionable steps with requirement references

=== STEP 3: SCAFFOLDING ===
✓ Created directory structure (15 directories)
✓ Generated configuration files (6 files)
✓ Created entry points (4 files)
✓ Setup testing infrastructure (3 files)

=== STEP 4: BOILERPLATE GENERATION ===
✓ Generated Backend:
  - 3 data models (User, Task, Project)
  - 9 API routes
  - 3 service files
  - 2 middleware files

✓ Generated Frontend:
  - 3 TypeScript interfaces
  - 9 API client functions
  - 6 component stubs
  - 3 custom hooks
  - 2 store slices

✓ Generated Utilities:
  - 3 validation schemas
  - 4 helper functions

Total: 52 files generated

=== NEXT STEPS ===
1. Run 'npm install' to install dependencies
2. Review generated files in apps/ directory
3. Start development servers:
   - Frontend: npm run dev (in apps/web)
   - Backend: npm run dev (in apps/api)
4. Begin implementing TODO items in service files
```

### Generation Failure Case

```
=== STEP 1: GENERATE DESIGN & TASKS ===
✗ Failed to analyze requirements.md

Error: Requirements file appears incomplete
- Missing user stories section
- No acceptance criteria found
- App description not provided

Status: GENERATION FAILED
Workflow stopped. Please complete requirements.md and save again.

Next Steps:
1. Add user stories with "As a [role], I want [feature], so that [benefit]" format
2. Include acceptance criteria for each user story
3. Provide app name and description in Introduction section
4. Save the file to trigger workflow again
```

## Error Handling

- **Validation Errors**: Stops workflow, provides detailed error report with file locations
- **Scaffolding Errors**: Reports which directories/files failed to create
- **Boilerplate Errors**: Reports which code generation steps failed
- **Partial Success**: Shows what was successfully created before failure

## Benefits

- **Ultimate Simplicity**: Fill ONLY requirements.md → complete app generated
- **Zero Manual Work**: design.md and tasks.md are auto-generated
- **Intelligent**: Infers architecture and data models from requirements
- **Safe**: Validates at each step before proceeding
- **Incremental**: Each step must succeed before next step runs
- **Informative**: Detailed output shows exactly what was created
- **Error-Friendly**: Clear error messages with actionable fixes

## Notes

- **You ONLY edit templates/requirements.md** - that's it!
- design.md and tasks.md are automatically generated from requirements
- This hook replaces the need to manually run four separate workflows
- Validation ensures you don't generate incomplete apps
- If you want more control, you can still run individual hooks manually
- The hook only runs when you save templates/requirements.md
- Existing generated files are overwritten with new versions
