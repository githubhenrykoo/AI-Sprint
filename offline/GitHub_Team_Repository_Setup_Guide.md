# GitHub Team Repository Setup Guide

## **Overview**
Simple guide for setting up GitHub accounts and team repositories for the hackathon.

## **GitHub Account Requirements**
- All students must have a GitHub account
- Use school email address for education benefits
- Set up SSH keys for secure access
- Configure Git with proper username and email

## **Team Repository Setup**

### **Step 1: Create Repository**
1. Team Technical Lead creates repository
2. Repository name: `hackathon-2025-[teamname]`
3. Set repository to public
4. Add all team members as collaborators
5. Create basic README file

### **Step 2: Repository Structure**
```
hackathon-2025-[teamname]/
├── README.md
├── docs/
│   ├── sessions/
│   └── individual-learning/
├── src/
│   ├── iot/
│   ├── pkc/
│   ├── telegram/
│   └── bmad/
└── config/
```

### **Step 3: Basic README Template**
```markdown
# Team [Name] - BBS AI Hackathon 2025

## Team Members
- **Technical Lead**: [Name] (@github-username)
- **Documentation Lead**: [Name] (@github-username)
- **Communication Lead**: [Name] (@github-username)
- **Quality Lead**: [Name] (@github-username)

## Project Description
[Brief description of your team's project]

## Technology Stack
- PKC (Personal Knowledge Container)
- ESP32 and IoT sensors
- Telegram Bot
- BMAD Method
- NotebookLM

## Getting Started
[Basic setup instructions]
```

## **Daily Usage**
- Commit code changes daily
- Document progress in `docs/sessions/`
- Individual learning in `docs/individual-learning/[your-name]/`
- Use NotebookLM for research and documentation

## **Basic Git Commands**
```bash
# Clone repository
git clone [repository-url]

# Daily workflow
git add .
git commit -m "Brief description of changes"
git push origin main

# Create feature branch (optional)
git checkout -b feature-name
git push origin feature-name
```

## **Git Submodules**
Teams will learn to use Git submodules for managing external dependencies:

```bash
# Add a submodule
git submodule add [repository-url] [folder-name]

# Clone repository with submodules
git clone --recursive [repository-url]

# Update submodules
git submodule update --init --recursive

# Pull latest changes in submodules
git submodule update --remote
```

### **Common Submodule Use Cases**
- BMAD Method framework integration
- Shared utility libraries between teams
- External IoT sensor libraries
- PKC configuration templates

## **Pull Requests**
Teams will learn collaborative development using pull requests:

### **Creating Pull Requests**
1. Create feature branch for your changes
2. Push branch to GitHub
3. Open pull request on GitHub website
4. Add description of changes
5. Request team review
6. Merge after approval

### **Pull Request Workflow**
```bash
# 1. Create and switch to feature branch
git checkout -b feature/new-sensor-integration

# 2. Make your changes and commit
git add .
git commit -m "Add temperature sensor integration"

# 3. Push branch to GitHub
git push origin feature/new-sensor-integration

# 4. Create pull request on GitHub website
# 5. Team reviews and approves
# 6. Merge pull request
```

### **Pull Request Best Practices**
- Use clear, descriptive branch names
- Write good pull request descriptions
- Keep changes focused and small
- Test your changes before creating PR
- Respond to review feedback promptly

## **Team Collaboration**
- All team members have write access
- Commit changes regularly
- Use clear commit messages
- Help teammates with Git issues
- Keep repository organized and clean
