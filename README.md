# Description:
***This instruction consists instructions for running Dockerfile, you can use it to create backups of your repository.*** <br>  <br>

# Requirements:
***This instruction assumes that you have Docker installed. <br>
   Have GitHub account. <br>
   Have created ssh-key and input to GitHub.<br><br><br>***

# Useful links:

[Docker](https://github.com/Jeka4el/DevOps-Task0/)  - use this link to see how to install Docker. <br>
[GitHub account](https://docs.github.com/en/get-started/onboarding/getting-started-with-your-github-account) - use this link to see how to cteate GitHub account. <br>
[Create ssh-key and it](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
[Task](https://absorbed-parrot-e34.notion.site/Task-1-DevOps-1-0-a7520340104248bea0e867b5e3ddfdfa) - use this link to read the task. <br><br><br>


`Step 1:` Clone this repository.

```
git clone https://github.com/Jeka4el/devops_intern_Jeka4el.git 

```


`Step 2:` Upload it to your private repo.

*Use this link if you don't know how to do it.*
```
https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository 
```


`Step 3:` Create a directory in your home directory that we will mount into the container.

```
mkdir -p "$PWD"/backup
```
*Henceforth we will call it the "mounted directory".*


`Step 4:` Add the ssh-key that you have created to the "mounted directory", The name has to be id_rsa.
```
cp repo_specific_key "$PWD"/backup/id_rsa
```
*Remember repo_specific_key is your ssh-key, use this command in the directory where your key is located.*



`Step 5:` Build a docker image.
```
docker build -t backup-script-container .
```
*Please use this command in the repository directory, that you have cloned.*



`Step 6:` Run your container
```
docker run -d -u root -v /home/ubuntu/backup:/root/backup backup-script-container
```


'Step 5:' Check the results
*where /home/ubuntu/backup is a dir when you want to see backups.* <br><br>

```
ls /home/ubuntu/backup
