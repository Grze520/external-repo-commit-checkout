External Repo Commit Checkout

This repository demonstrates a GitHub Actions workflow that checks out a specific commit from an external repository and 
performs actions based on its contents. The project serves as an example of how to automate tasks with GitHub Actions, 
specifically by checking out and working with a specific commit from an external repository.

Overview

The workflow completes the following tasks:

    1. Checkout an external repository: The workflow clones an external GitHub repository and checks out a specific commit.
    2. Process files in the repository: After checking out the repository, the workflow reads and outputs the content 
       of a specific file (greeting.txt).

Workflow Steps

    1. Trigger: The workflow is triggered by a push event.
    2. Checkout external repository: The workflow uses the actions/checkout@v3 action to checkout the repository 
       abystoma/external-workflow at the commit 3eb718710f20d7df6874acdc41e189a2ae4182f5.
    3. Display the content of greeting.txt: The workflow outputs the content of the greeting.txt file found in the 
       checked-out commit.

YAML Workflow Example:

    name: commit_checkout

    on: [push]

    jobs:
      external-workflow:
        runs-on: ubuntu-latest

        steps:
          # Step 1: Checkout the external repository at a specific commit
          - name: Checkout external repository
            uses: actions/checkout@v3
            with:
              repository: abystoma/external-workflow
              ref: 3eb718710f20d7df6874acdc41e189a2ae4182f5

          # Step 2: Display the contents of the greeting.txt file
          - name: Greetings
            run: echo "$(<greeting.txt)"

How to Use

    1. Clone the repository:
    git clone https://github.com/Grze520/external-repo-commit-checkout.git
    2. Customize the workflow: You can modify the workflow to checkout other repositories or commits by updating the 
    repository and ref fields in the YAML workflow.
    3. Run the workflow: Push changes to your GitHub repository, and check the workflow execution in the Actions tab on 
    GitHub.  

Output

When the workflow runs, it will checkout the specified commit from the external repository. If the greeting.txt file 
exists in that commit, its contents will be printed as part of the job's output.

Technologies Used

    * GitHub Actions: Automating workflows and tasks.
    * Bash: Shell commands used in the workflow to process files.
    * YAML: Used to define GitHub Actions workflows.

License

This project is licensed under the MIT License.
See the LICENSE file for more details.
