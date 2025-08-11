### **Session 1**

- Introduction to the program
-> brief overview on program structure
- Introducing the speakers
- Brief Introduction to AI and LLM
-> Interactive session asking have they ever used AI, what did they use it for, What do they know about it?
- Introduction to PKC
-> brief intro what PKC is, list the principles and brief introduction on its importance
- Introduction to IoT (demonstration)
-> definition of IoT and examples of its use case
- Introduction on how to combine IoT and PKC and its principles
- Brief summary on session 1
- List all the tools that needs to be installed/signed up for session 2 (NotebookLM)

### **Session 2**

- [30 mins prior] Helping with the installation/sign up process
- Brief Review on session 1 topics
- Demonstration on NotebookLM
-> Give some time for the participants to try it themselves
- Brief explanation on NotebookLM
-> Its advantages/disadvantages, RAG(?), needs to be online
- Brief explanation on what PKC can do better (comparing the PKC by adding 200/300 diff sources -> comparing the amount of sources notebookLM vs PKC)
- Demonstration on PKC
- Let them know that they too will be able to do this within the hackathon
- Brief explanation of Local-First principles + Data sovereignty
- Brief Summary on Session 2
- List all the tools that might be needed for session 3 (zerotier)

### Session 3

- [30 mins prior] Helping with the installation
- Brief Review on session 2 topics
- Demonstration on online TOSIOS
-> ask them to join
-> Explain that the game was online
- Explain that we can host the game offline
-> ask them to join
-> explain why they can't
- Explain a bit about zerotier
- Demonstration of them joining zerotier + playing the game offline (make it into groups (free zerotier limitation))
- Further explanation on local-first principle
- Further explanation on how it works offline (docker-compose.yml, etc)
- Summary
- List all tools needed for session 4 (windsurf, docker)

### Session 4

- [30 mins prior] Helping with the installation
- Brief review on sess 3 topics
- Demonstration on Docker 1 -> Hosting TOSIOS
-> Also review on zerotier
- Brief explanation on Docker + its importance
- Demonstration on Docker 2 -> hosting own PKC
-> Explanation on why they haven't been able to use the PKC -> lack of Ollama
- Demonstration on Docker 3 -> hosting something else
- Advantage of Docker
- Summary
- Tools for upcoming session (Ollama + 1 specified LLM (qwen 0.6b))

### Session 5

- [30 mins prior] Helping with the installation
- Review on sess 4
- Ollama demonstration on terminal
-> Let them explore and having fun
- Explain benefits of having their own Ollama and LLM
- Explain the LLM and their differences (size, usage, etc)
- Explain the biggest size each computer can run and how to find them for each computer
- Let them explore and download 1 additional LLM
-> while waiting the completion of the download, give demonstration on Ollama + PKC
- Explain how to switch LLM
- Summary

### Session 6

- [30 mins prior] Helping with the installation
- Review on sess 5
- Implement to complete system (PKC + LLM + RAG + database + etc)
-> Using Alessandro's API
-> Let them try to host using Alessandro's API
- Explain PKC infrastructure
- Explain why they need their own separate API
- Brief explanation on API
-> Explain what apps are accessible thru API and its importance
- Brief explanation on security
- Summary
- Tools for upcoming session (Notion, Google cloud)

### Session 7

- [30 mins prior] Helping with the installation
- Review on sess 6
- Demonstration on Ollama + PKC using Alessandro's API
-> Let them know that they need to change it to their own API
- Hands on tutorial on how to obtain API for google apps
-> Including which apps are enabled/disabled
-> First try to enable only the gdocs
- Explain the difference between those API keys and how to put them in the .env
- Try to launch PKC using their own API
-> See that now the gdocs works but gcal doesn't on the PKC
-> Explain that API only works for specific application
-> Enable gcals
-> Check that now both gdocs and gcal works
-> Check that notion still doesn't work
-> let them have fun
- Summary

### Session 8

- [30 mins prior] Helping with the installation
- Review on session 7
- Hands on tutorial on how to get Notion API
- Explain the difference between those API keys and how to put them in the .env
- Now try to launch the PKC with notion API only
-> Check that notion function works, but google apps doesn't
- Launch PKC with notion + google API
-> Check that both functionalities work
-> Let them explore the PKC
- Summary

