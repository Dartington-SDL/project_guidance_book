# Collaborative quantitative project workflows

Collaborative programming takes coordination and organisation. Adhering to a few simple principles will make this process work (reasonably) smoothly

## Designing the code structure

The first thing to do is to design the code structure based on the project protocol. This will allow you to determine, monitor and assign tasks as you proceed through the project.

In true DSDL style, Miro is a useful tool for mapping out the code structure. This map should include:
- The data engineering, cleaning, modelling, analysis and visualisation tasks to be completed
- The functions that you expect will need to be created within each task

The map should be organised in chronological order of task completion

This map can then be translated into a tabular format to support the assignment and monitoring of tasks across the team

## Project team

There are a couple of roles that need to be fulfilled in a project to facilitate organisation

### Roles and tasks

- Task assignment and monitoring: One person needs to be responsible for assigning tasks, monitoring their status and updating the status of the task in the task table
- Code review: All team members should participate in code reviews. These should be conducted at all major milestones in the project. The aim of a code review is to ensure the quality of the code is consistent across the project. Code structure, naming conventions, bugs and issues can be assessed and discussed
- Pull requests and merges: This is an important task as it is the point where code is reviewed, tested and then merged into the main project branch. Ideally one person is responsible for reviewing pull requests for testing and conducting that testing. A second person is then responsible for reviewing the tested code and merging it with the main branch. More on this in the next section

## Collaborative programming cycle

An example of how the Git workflow should work with a main branch, a test branch and two contributors working on features on their local branches

![Git workflow example](/assests/images/git_workflows.jpg "Git workflows example")

This process repeats until all tasks are completed