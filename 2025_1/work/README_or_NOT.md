# README_or_NOT
## 1. Quick Overview:
- This small 'project' is done in 5 Jupyter Notebooks, each corresponding to a specific task in order.
- All notebooks have some texts in the form of markdown or comments to explain the env set up, and what is being done. This README is for more comprehensive explanation and I write it only because I got bored when waiting Task 5 to run fully.(on CPU because of imcompatibility of Python ver. and package 'cuda') BTW it takes about 50 mins to run a whole round.
- Listed below are some points that are not required, or I just want to write them for (perhaps not my) future reference.

## 2. Environment Setup:
1. The whole work was done in VSCode with extensions:
    - Python
    - Jupyter
    - Github Copilot
2. Involved programs are mostly installed and managed using Scoop, like:
    - Python 3.13.7
    - Git
    - Nodejs
3. Since I don't have many packages to manage, I just installed them globally using pip, like:
    - torch
    - transformers
    - datasets
    - umap-learn
    - matplotlib
    - (more in the notebooks)
4. The trajectory of the project is well maintained using Git and Github, see:
    `https://github.com/Ortunate/AI_Pi_Entrance_Test/tree/main/2025_1/work`

## 3. Review:
0. BTW I have done a little project and a little learning when visiting NUS(for fun), so a lot of the knowledge involved like optimizer adam, latent space, and CNN are not too new to me. But I'm still a newbie.
1. Time was limited, at first I could dare to read the package documentations(like for numpy and pandas), but soon later I gave up systematically learning them, which is just as expected before getting down to work--we only had a week, after all.
2. Then I relied more on Copilot to:
    - catch up the concepts and mechanisms of involved knowledge.
    - help me call package functions and show me what their parameters are and do.
    - help me check for bugs, but usually very inefficient.
    - help me write comments and some texts, or LaTeX formulas, which saves me a lot of time.
3. But it's still hard, even if AI has much knowledge of related fields. For example, it doesn't know whether or not an api is obsolete. It even made up some apis that don't exist, and made mistakes in simple things like package importing.
4. Yet still, it improves my learning efficiency greatly. To free people from heavy labor, is also one of my motivations to learn AI.
5. Another thing is, I started sequentially. The first ones took at most half a day to finish, but the last one truly got me. Just downloading the dataset took me an hour, not to mention the code runs slowly on CPU. It wasted me a long time debugging for many reasons. Thank god I eventually made it.
6. So during this process, I contacted a lot of new knowledge and tried package callings that I have never used before.

- After writting all these, Task 5 is still running and needs like 15 more mins.