# AI Sprint Program - Session Material Reading List

This document organizes all reading materials by session to provide a structured learning progression throughout the AI Sprint program.

## Session 1: Introduction to AI and PKC Fundamentals

### Core Materials:
- **LLM_Large_Language_Models.md** - Essential foundation on Large Language Models
  - Covers training process, generation capabilities, and how LLMs function
  - Explores differences between local and cloud models
  - Discusses limitations and future developments

- **PKC_Personal_Knowledge_Container.md** - Introduction to Personal Knowledge Containers
  - Explains core concepts and architecture
  - Highlights data sovereignty principles
  - Demonstrates the local-first approach

### Supplementary Materials:
- **RAG_Retrieval_Augmented_Generation.md** - For participants interested in how AI can work with their personal data

### Video Resources:
- [Large Language Models explained briefly](https://www.youtube.com/watch?v=LPZh9BOjkQs) - Detailed explanation of LLMs
- [What is Retrieval-Augmented Generation (RAG)?](https://www.youtube.com/watch?v=T-D1OfcDW1M) - Brief RAG overview
- [RAG Explained](https://www.youtube.com/watch?v=qppV3n3YlF8) - Deeper dive into RAG

### Project Resources:
- [PKC Project GitHub Repository](https://github.com/githubhenrykoo/PKC) - Source code and documentation

### Learning Objectives:
- Understand what Large Language Models are and how they work
- Recognize the differences between cloud-based and local AI models
- Grasp the foundational principles of Personal Knowledge Containers
- Appreciate the importance of data sovereignty and local-first approaches
- Prepare for hands-on activities in the following sessions

---

## Session 2: Version Control and Collaboration

### Core Materials:
- **Git_Version_Control.md** - Complete guide to Git and version control
  - Explains core Git concepts (commits, branches, repositories)
  - Covers common workflows and best practices
  - Demonstrates basic and advanced Git operations
  - Addresses troubleshooting and collaboration strategies

### Supplementary Materials:
- **MCard_Content_Addressable_Storage.md** - For understanding content-addressable storage principles similar to Git's internal architecture

### Learning Objectives:
- Master Git fundamentals for project collaboration
- Understand distributed version control concepts and workflows
- Learn how to manage code history and collaborate with others
- Compare Git's approach to other content-addressable storage systems
- Prepare for collaborative development work in later sessions
- Appreciate the relationship between version control and local-first applications

---

## Session 3: Networking and Connectivity

### Core Materials:
- **ZeroTier_Virtual_Networking.md** - Software-defined networking fundamentals
  - Explains ZeroTier architecture and functionality
  - Compares centralized vs. peer-to-peer networking
  - Details installation and configuration process
  - Discusses practical applications and use cases

### Supplementary Materials:
- **Overlay_VPN_Virtual_Private_Networks.md** - VPN architecture and concepts
  - Provides historical context for virtual networking
  - Explains technical differences between traditional and overlay VPNs
  - Discusses security considerations and implementation strategies

- **NetBird_Open_Source_VPN.md** - Open-source VPN alternatives
  - Describes another approach to virtual networking
  - Compares with ZeroTier for broader understanding

### Video Resources:
- [ZeroTier Simple Network Setup](https://www.youtube.com/watch?v=EPYUOkxgiCA) - Step-by-step setup guide
- [How does ZeroTier actually work?](https://www.youtube.com/watch?v=Lao9T_RQTak) - Technical explanation

### Project Resources:
- [TOSIOS GitHub Repository](https://github.com/halftheopposite/TOSIOS) - The Open-Source IO Shooter game used for demonstration

### Learning Objectives:
- Understand virtual networking concepts and implementation
- Master ZeroTier setup and configuration for peer connectivity
- Learn how devices can communicate securely across different networks
- Appreciate the advantages of mesh networking vs. traditional approaches
- Prepare for the Session 3 gaming demonstration using ZeroTier
- Develop skills for deploying distributed and local-first applications

---

## Session 4: Containerization with Docker

### Core Materials:
- **PKC_deployment.md** - Step-by-step guide to deploy PKC using Docker
- **TOSIOS Docker Deployment Guide** *(to be created)* - Step-by-step instructions for containerizing the game

### Practical Exercise:
- **Download TOSIOS Game**: Students will download [TOSIOS GitHub Repository](https://github.com/halftheopposite/TOSIOS) to their local computers
- **Docker Containerization**: Learn to deploy the downloaded game using Docker containers
- **Local Development Setup**: Configure the game environment using containerization

### Video Resources:

#### Installation Guides:
- [Docker Installation on Windows](https://www.youtube.com/watch?v=JBEUKrjbWqg) - Step-by-step Windows installation
- [Docker Installation on Mac](https://www.youtube.com/watch?v=-y1BmDbcaEU) - Step-by-step Mac installation

#### Docker Concepts:
- [Docker in 100 Seconds](https://www.youtube.com/watch?v=Gjnup-PuquQ) - Quick introduction
- [What is Docker in 5 minutes](https://www.youtube.com/watch?v=_dfLOzuIg2o) - Visual explanation of Docker concepts

### Learning Objectives:
- Understand container technology fundamentals through hands-on practice
- Learn Docker basics by containerizing a real-world application (TOSIOS game)
- Master local application deployment using Docker
- Prepare for distributed gaming scenarios using containerized applications
- Bridge the gap between Session 3 networking concepts and practical deployment

### Optional Reading:
- **Docker_Containerization.md** - Comprehensive guide to Docker containerization concepts (optional for deeper understanding)

---

## Session 5: Ollama Setup and Exploration

### Core Materials:
- **Ollama_Usage_Guide.md** - How Ollama works and detailed usage instructions

### Practical Exercise:
- **Install Ollama**: Students will install Ollama on their local machines
- **Configure LLM Models**: Set up and download language models through Ollama
- **Test PKC Integration**: Ensure PKC deployment from Session 4 works with Ollama
- **Hands-on LLM Usage**: Practice using local language models

### Video Resources:
- [Ollama Installation and Setup Guide](https://www.youtube.com/watch?v=UtSSMs6ObqY) - Complete Ollama setup tutorial

### Learning Objectives:
- Understand Large Language Model fundamentals and capabilities
- Master Ollama installation and configuration
- Learn to run local AI models on personal computers
- Verify PKC system integration with local LLMs
- Gain hands-on experience with privacy-preserving AI tools
- Bridge containerized applications (Session 4) with AI capabilities

### Optional Materials:
- **LLM_Large_Language_Models.md** - Introduction to Large Language Models concepts and applications
- **Ollama_Basic_Commands.md** - Essential Ollama commands and usage guide

---

## Session 6: PKC Deployment and Environment Configuration

### Core Materials:
- **PKC_Deployment_Guide.md** - Comprehensive guide to deploying PKC using Docker
- **PKC_Environment_Configuration.md** - Detailed guide for configuring PKC environment variables
- **PKC_Troubleshooting_Guide.md** - Common issues and solutions for PKC deployment

### Practical Exercise:
- **Deploy PKC**: Follow step-by-step instructions to deploy PKC locally
- **Configure Environment**: Set up and verify the .env file with proper configuration
- **Verify Installation**: Ensure all components are running correctly
- **Basic Operations**: Learn to use PKC's core features
- **Troubleshooting**: Practice identifying and resolving common issues

### Learning Objectives:
- Master PKC deployment using Docker
- Understand containerized application architecture
- Learn to configure and manage environment variables
- Develop troubleshooting skills for containerized applications
- Gain hands-on experience with PKC's features and capabilities

### Optional Reading:
- **Docker_Containerization.md** - In-depth look at Docker concepts
- **Git_Version_Control.md** - For managing PKC configurations and customizations

---

## Session 7: Environment Configuration and Management

### Core Materials:
- **Environment_Variables_Guide.md** - Comprehensive guide to PKC environment configuration

### Practical Exercise:
- **Environment Setup**: Configure the `.env` file with required settings
- **Configuration Testing**: Verify environment variables are properly loaded
- **Environment Management**: Understand different configuration profiles
- **Security Practices**: Learn to protect sensitive configuration data
- **Troubleshooting**: Debug common environment-related issues

### Learning Objectives:
- Understand the role of environment variables in PKC
- Master the configuration of PKC through environment variables
- Learn best practices for managing sensitive configuration
- Develop skills for troubleshooting configuration issues
- Implement secure environment management practices

### Optional Reading:
- **Docker_Containerization.md** - For understanding container environment management
- **Git_Version_Control.md** - For managing configuration files in version control

---

## Session 8: APIs and Google API Integration

### Core Materials:
- **What_is_API.md** - Comprehensive guide to understanding APIs and their importance
- **Google_API_Integration.md** - Detailed documentation on Google API usage and integration

### Practical Exercise:
- **API Fundamentals**: Learn the basics of API architecture and communication
- **Google API Setup**: Configure Google Cloud Console and API credentials
- **API Integration**: Implement Google API calls in applications
- **Error Handling**: Manage API responses and handle errors gracefully
- **Security Practices**: Implement secure API authentication and usage

### Learning Objectives:
- Understand what APIs are and why they are important in modern software development
- Master the fundamentals of REST API architecture and communication protocols
- Learn to work with Google APIs including authentication and authorization
- Develop skills for integrating third-party APIs into applications
- Implement best practices for API security and error handling

### Optional Reading:
- **API_Application_Programming_Interface.md** - For deeper understanding of API concepts
- **RAG_Retrieval_Augmented_Generation.md** - For understanding API usage in AI applications

---

