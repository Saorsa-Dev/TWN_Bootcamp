# Module 3: Version Control with Git

Version control or Source control is the practice of tracking and managing software code, enabling multiple people to work simultaneously in the same repository on a project. Code is hosted centrally on the internet and developers clone code down to local machines. Git is the most popular version control system.

### Basic concepts:

1. Remote Git repository: where code is hosted, e.g. GitHub or GitLab
2. Local Git repository: local cloned copy on machine
3. Git client: can be UI or command line
4. Use push/pull to retrieve and send code between local and server
5. Merge conflicts may occur when same code edited by multiple people, need to resolve manually - avoid by pushing/pulling from source regularly

### Branching concepts:

1. Enable better collaboration
2. Main branch is default branch - kept stable always ready for production deployment
3. Create temporary branches for feature or bug fix - common names: dev, feature, bugfix, e.g. bufix/ticket-2134 (short/descriptive)
4. Based on main branch, start from same code base
5. Merge back to main on completion
6. Merge/pull requests: code review by peer/senior before merging back into main -- approve or decline

### Git for Devops

Keeps your scripts tracked and versioned by Git, and can be shared with the wider team.

Use Case # 1 = Infrastructure as Code Create and provision infrastructure
Use Case # 2 - Automation scripts
Use Case # 3 - CI/CD Pipeline and Build Automation

CI means: on each merge, checkout code from repository, test and build application. For this need integration between build automation tool and git repository.

### Main best practices

1. Use descriptive/meaningful commit messages
2. Commit in small-ish chunks where possible
3. Commit only related work
4. Pull often from remote git repo
5. Merge branches into main often
6. Don't git push straight to main - set up merge/pull requests for peer review
7. Use .gitignore to ignore files/folders you do not want to sync to remote repo


