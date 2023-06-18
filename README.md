# Домашнее задание к занятию 10 «Jenkins»

## Подготовка к выполнению

1. Создать два VM: для jenkins-master и jenkins-agent.
2. Установить Jenkins при помощи playbook.
3. Запустить и проверить работоспособность.
4. Сделать первоначальную настройку.

## Основная часть

1. Сделать Freestyle Job, который будет запускать `molecule test` из любого вашего репозитория с ролью.  
Console output:
`Started by user unknown or anonymous
Running as SYSTEM
Building remotely on agent (linux ansible) in workspace /opt/jenkins_agent/workspace/freestyle molecule test
The recommended git tool is: NONE
No credentials specified
 > git rev-parse --resolve-git-dir /opt/jenkins_agent/workspace/freestyle molecule test/.git # timeout=10
Fetching changes from the remote Git repository
 > git config remote.origin.url https://github.com/juls-blekh/08-ansible-05-testing.git # timeout=10
Fetching upstream changes from https://github.com/juls-blekh/08-ansible-05-testing.git
 > git --version # timeout=10
 > git --version # 'git version 2.30.2'
 > git fetch --tags --force --progress -- https://github.com/juls-blekh/08-ansible-05-testing.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse refs/remotes/origin/master^{commit} # timeout=10
Checking out Revision 38b151940bb40fe38f2c6cf1c6f63c0c6a325741 (refs/remotes/origin/master)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 38b151940bb40fe38f2c6cf1c6f63c0c6a325741 # timeout=10
Commit message: "Update README.md"
 > git rev-list --no-walk 38b151940bb40fe38f2c6cf1c6f63c0c6a325741 # timeout=10
[freestyle molecule test] $ /bin/sh -xe /tmp/jenkins16994564273963990872.sh
+ pip3 install molecule==3.5.2
Requirement already satisfied: molecule==3.5.2 in /usr/local/lib/python3.9/dist-packages (3.5.2)
Requirement already satisfied: selinux in /usr/local/lib/python3.9/dist-packages (from molecule==3.5.2) (0.3.0)
Requirement already satisfied: PyYAML<6,>=5.1 in /usr/local/lib/python3.9/dist-packages (from molecule==3.5.2) (5.4.1)
Requirement already satisfied: Jinja2>=2.11.3 in /usr/local/lib/python3.9/dist-packages (from molecule==3.5.2) (3.1.2)
Requirement already satisfied: cookiecutter>=1.7.3 in /usr/local/lib/python3.9/dist-packages (from molecule==3.5.2) (2.1.1)
Requirement already satisfied: rich>=9.5.1 in /usr/local/lib/python3.9/dist-packages (from molecule==3.5.2) (13.3.5)
Requirement already satisfied: click<9,>=8.0 in /usr/local/lib/python3.9/dist-packages (from molecule==3.5.2) (8.1.3)
Requirement already satisfied: click-help-colors>=0.9 in /usr/local/lib/python3.9/dist-packages (from molecule==3.5.2) (0.9.1)
Requirement already satisfied: subprocess-tee>=0.3.5 in /usr/local/lib/python3.9/dist-packages (from molecule==3.5.2) (0.4.1)
Requirement already satisfied: paramiko<3,>=2.5.0 in /usr/local/lib/python3.9/dist-packages (from molecule==3.5.2) (2.12.0)
Requirement already satisfied: packaging in /usr/local/lib/python3.9/dist-packages (from molecule==3.5.2) (23.1)
Requirement already satisfied: pluggy<2.0,>=0.7.1 in /usr/local/lib/python3.9/dist-packages (from molecule==3.5.2) (1.0.0)
Requirement already satisfied: cerberus!=1.3.3,!=1.3.4,>=1.3.1 in /usr/local/lib/python3.9/dist-packages (from molecule==3.5.2) (1.3.2)
Requirement already satisfied: ansible-compat>=0.5.0 in /usr/local/lib/python3.9/dist-packages (from molecule==3.5.2) (3.0.2)
Requirement already satisfied: enrich>=1.2.5 in /usr/local/lib/python3.9/dist-packages (from molecule==3.5.2) (1.2.7)
Requirement already satisfied: jsonschema>=4.6.0 in /usr/local/lib/python3.9/dist-packages (from ansible-compat>=0.5.0->molecule==3.5.2) (4.17.3)
Requirement already satisfied: ansible-core>=2.12 in /usr/local/lib/python3.9/dist-packages (from ansible-compat>=0.5.0->molecule==3.5.2) (2.14.6)
Requirement already satisfied: cryptography in /usr/lib/python3/dist-packages (from ansible-core>=2.12->ansible-compat>=0.5.0->molecule==3.5.2) (3.3.2)
Requirement already satisfied: resolvelib<0.9.0,>=0.5.3 in /usr/local/lib/python3.9/dist-packages (from ansible-core>=2.12->ansible-compat>=0.5.0->molecule==3.5.2) (0.8.1)
Requirement already satisfied: setuptools in /usr/lib/python3/dist-packages (from cerberus!=1.3.3,!=1.3.4,>=1.3.1->molecule==3.5.2) (52.0.0)
Requirement already satisfied: requests>=2.23.0 in /usr/local/lib/python3.9/dist-packages (from cookiecutter>=1.7.3->molecule==3.5.2) (2.30.0)
Requirement already satisfied: jinja2-time>=0.2.0 in /usr/local/lib/python3.9/dist-packages (from cookiecutter>=1.7.3->molecule==3.5.2) (0.2.0)
Requirement already satisfied: binaryornot>=0.4.4 in /usr/local/lib/python3.9/dist-packages (from cookiecutter>=1.7.3->molecule==3.5.2) (0.4.4)
Requirement already satisfied: python-slugify>=4.0.0 in /usr/local/lib/python3.9/dist-packages (from cookiecutter>=1.7.3->molecule==3.5.2) (8.0.1)
Requirement already satisfied: chardet>=3.0.2 in /usr/lib/python3/dist-packages (from binaryornot>=0.4.4->cookiecutter>=1.7.3->molecule==3.5.2) (4.0.0)
Requirement already satisfied: MarkupSafe>=2.0 in /usr/local/lib/python3.9/dist-packages (from Jinja2>=2.11.3->molecule==3.5.2) (2.1.2)
Requirement already satisfied: arrow in /usr/local/lib/python3.9/dist-packages (from jinja2-time>=0.2.0->cookiecutter>=1.7.3->molecule==3.5.2) (1.2.3)
Requirement already satisfied: pyrsistent!=0.17.0,!=0.17.1,!=0.17.2,>=0.14.0 in /usr/local/lib/python3.9/dist-packages (from jsonschema>=4.6.0->ansible-compat>=0.5.0->molecule==3.5.2) (0.19.3)
Requirement already satisfied: attrs>=17.4.0 in /usr/local/lib/python3.9/dist-packages (from jsonschema>=4.6.0->ansible-compat>=0.5.0->molecule==3.5.2) (23.1.0)
Requirement already satisfied: pynacl>=1.0.1 in /usr/local/lib/python3.9/dist-packages (from paramiko<3,>=2.5.0->molecule==3.5.2) (1.5.0)
Requirement already satisfied: six in /usr/lib/python3/dist-packages (from paramiko<3,>=2.5.0->molecule==3.5.2) (1.16.0)
Requirement already satisfied: bcrypt>=3.1.3 in /usr/local/lib/python3.9/dist-packages (from paramiko<3,>=2.5.0->molecule==3.5.2) (4.0.1)
Requirement already satisfied: cffi>=1.4.1 in /usr/local/lib/python3.9/dist-packages (from pynacl>=1.0.1->paramiko<3,>=2.5.0->molecule==3.5.2) (1.15.1)
Requirement already satisfied: pycparser in /usr/local/lib/python3.9/dist-packages (from cffi>=1.4.1->pynacl>=1.0.1->paramiko<3,>=2.5.0->molecule==3.5.2) (2.21)
Requirement already satisfied: text-unidecode>=1.3 in /usr/local/lib/python3.9/dist-packages (from python-slugify>=4.0.0->cookiecutter>=1.7.3->molecule==3.5.2) (1.3)
Requirement already satisfied: certifi>=2017.4.17 in /usr/lib/python3/dist-packages (from requests>=2.23.0->cookiecutter>=1.7.3->molecule==3.5.2) (2020.6.20)
Requirement already satisfied: urllib3<3,>=1.21.1 in /usr/lib/python3/dist-packages (from requests>=2.23.0->cookiecutter>=1.7.3->molecule==3.5.2) (1.26.5)
Requirement already satisfied: idna<4,>=2.5 in /usr/lib/python3/dist-packages (from requests>=2.23.0->cookiecutter>=1.7.3->molecule==3.5.2) (2.10)
Requirement already satisfied: charset-normalizer<4,>=2 in /usr/local/lib/python3.9/dist-packages (from requests>=2.23.0->cookiecutter>=1.7.3->molecule==3.5.2) (3.1.0)
Requirement already satisfied: pygments<3.0.0,>=2.13.0 in /usr/local/lib/python3.9/dist-packages (from rich>=9.5.1->molecule==3.5.2) (2.15.1)
Requirement already satisfied: markdown-it-py<3.0.0,>=2.2.0 in /usr/local/lib/python3.9/dist-packages (from rich>=9.5.1->molecule==3.5.2) (2.2.0)
Requirement already satisfied: mdurl~=0.1 in /usr/local/lib/python3.9/dist-packages (from markdown-it-py<3.0.0,>=2.2.0->rich>=9.5.1->molecule==3.5.2) (0.1.2)
Requirement already satisfied: python-dateutil>=2.7.0 in /usr/lib/python3/dist-packages (from arrow->jinja2-time>=0.2.0->cookiecutter>=1.7.3->molecule==3.5.2) (2.8.1)
Requirement already satisfied: distro>=1.3.0 in /usr/lib/python3/dist-packages (from selinux->molecule==3.5.2) (1.5.0)
+ molecule --version
molecule [1;32m3.5[0m[32m.[0m[1;32m2[0m using python [1;36m3.9[0m 
    [33mansibl[0m[1;33me[0m[1;2;92m:[0m[1;36m2[0m[1;36m.[0m[1;36m14.6[0m
    [33mdelegat[0m[1;33med[0m[1;2;92m:[0m[1;36m3[0m[1;36m.[0m[1;36m5.2[0m[2m from molecule[0m
    [33mdocker[0m[2m:[0m[1;36m2.1[0m[1;36m.[0m[1;36m0[0m[2m from molecule_docker[0m requiring collections: community.docker>=[1;36m3.0[0m.[1;36m2[0m ansible.posix>=[1;36m1.4[0m.[1;36m0[0m
+ cd roles/vector-role
+ molecule test
[34mINFO    [0m default scenario test matrix: dependency, lint, cleanup, destroy, syntax, create, prepare, converge, idempotence, side_effect, verify, cleanup, destroy
[34mINFO    [0m Performing prerun[33m...[0m
[34mINFO    [0m Set [33mANSIBLE_LIBRARY[0m=[35m/root/.cache/ansible-compat/f5bcd7/[0m[95mmodules[0m:[35m/root/.ansible/plugins/[0m[95mmodules[0m:[35m/usr/share/ansible/plugins/[0m[95mmodules[0m
[34mINFO    [0m Set [33mANSIBLE_COLLECTIONS_PATH[0m=[35m/root/.cache/ansible-compat/f5bcd7/[0m[95mcollections[0m:[35m/root/.ansible/[0m[95mcollections[0m:[35m/usr/share/ansible/[0m[95mcollections[0m
[34mINFO    [0m Set [33mANSIBLE_ROLES_PATH[0m=[35m/root/.cache/ansible-compat/f5bcd7/[0m[95mroles[0m:[35m/root/.ansible/[0m[95mroles[0m:[35m/usr/share/ansible/[0m[95mroles[0m:[35m/etc/ansible/[0m[95mroles[0m
[34mINFO    [0m [2;36mRunning [0m[2;32mdefault[0m[2;36m > [0m[2;32mdependency[0m
[31mWARNING [0m Skipping, missing the requirements file.
[31mWARNING [0m Skipping, missing the requirements file.
[34mINFO    [0m [2;36mRunning [0m[2;32mdefault[0m[2;36m > [0m[2;32mlint[0m
[34mINFO    [0m Lint is disabled.
[34mINFO    [0m [2;36mRunning [0m[2;32mdefault[0m[2;36m > [0m[2;32mcleanup[0m
[31mWARNING [0m Skipping, cleanup playbook not configured.
[34mINFO    [0m [2;36mRunning [0m[2;32mdefault[0m[2;36m > [0m[2;32mdestroy[0m
[34mINFO    [0m Sanity checks: [32m'docker'[0m

PLAY [Destroy] *****************************************************************

TASK [Set async_dir for HOME env] **********************************************
[32mok: [localhost][0m

TASK [Destroy molecule instance(s)] ********************************************
[33mchanged: [localhost] => (item=instance)[0m
[33mchanged: [localhost] => (item=ubuntu)[0m

TASK [Wait for instance(s) deletion to complete] *******************************
[32mok: [localhost] => (item=instance)[0m
[32mok: [localhost] => (item=ubuntu)[0m

TASK [Delete docker networks(s)] ***********************************************
[36mskipping: [localhost][0m

PLAY RECAP *********************************************************************
[33mlocalhost[0m                  : [32mok=3   [0m [33mchanged=1   [0m unreachable=0    failed=0    [36mskipped=1   [0m rescued=0    ignored=0

[34mINFO    [0m [2;36mRunning [0m[2;32mdefault[0m[2;36m > [0m[2;32msyntax[0m

playbook: /opt/jenkins_agent/workspace/freestyle molecule test/roles/vector-role/molecule/default/converge.yml
[34mINFO    [0m [2;36mRunning [0m[2;32mdefault[0m[2;36m > [0m[2;32mcreate[0m

PLAY [Create] ******************************************************************

TASK [Set async_dir for HOME env] **********************************************
[32mok: [localhost][0m

TASK [Log into a Docker registry] **********************************************
[36mskipping: [localhost] => (item=None) [0m
[36mskipping: [localhost] => (item=None) [0m
[36mskipping: [localhost][0m

TASK [Check presence of custom Dockerfiles] ************************************
[32mok: [localhost] => (item={'image': 'docker.io/pycontribs/centos:7', 'name': 'instance', 'pre_build_image': True})[0m
[32mok: [localhost] => (item={'image': 'docker.io/pycontribs/ubuntu:latest', 'name': 'ubuntu', 'pre_build_image': True})[0m

TASK [Create Dockerfiles from image names] *************************************
[36mskipping: [localhost] => (item={'image': 'docker.io/pycontribs/centos:7', 'name': 'instance', 'pre_build_image': True})[0m
[36mskipping: [localhost] => (item={'image': 'docker.io/pycontribs/ubuntu:latest', 'name': 'ubuntu', 'pre_build_image': True})[0m
[36mskipping: [localhost][0m

TASK [Synchronization the context] *********************************************
[36mskipping: [localhost] => (item={'image': 'docker.io/pycontribs/centos:7', 'name': 'instance', 'pre_build_image': True})[0m
[36mskipping: [localhost] => (item={'image': 'docker.io/pycontribs/ubuntu:latest', 'name': 'ubuntu', 'pre_build_image': True})[0m
[36mskipping: [localhost][0m

TASK [Discover local Docker images] ********************************************
[32mok: [localhost] => (item={'changed': False, 'skipped': True, 'skip_reason': 'Conditional result was False', 'item': {'image': 'docker.io/pycontribs/centos:7', 'name': 'instance', 'pre_build_image': True}, 'ansible_loop_var': 'item', 'i': 0, 'ansible_index_var': 'i'})[0m
[32mok: [localhost] => (item={'changed': False, 'skipped': True, 'skip_reason': 'Conditional result was False', 'item': {'image': 'docker.io/pycontribs/ubuntu:latest', 'name': 'ubuntu', 'pre_build_image': True}, 'ansible_loop_var': 'item', 'i': 1, 'ansible_index_var': 'i'})[0m

TASK [Build an Ansible compatible image (new)] *********************************
[36mskipping: [localhost] => (item=molecule_local/docker.io/pycontribs/centos:7) [0m
[36mskipping: [localhost] => (item=molecule_local/docker.io/pycontribs/ubuntu:latest)[0m
[36mskipping: [localhost][0m

TASK [Create docker network(s)] ************************************************
[36mskipping: [localhost][0m

TASK [Determine the CMD directives] ********************************************
[32mok: [localhost] => (item={'image': 'docker.io/pycontribs/centos:7', 'name': 'instance', 'pre_build_image': True})[0m
[32mok: [localhost] => (item={'image': 'docker.io/pycontribs/ubuntu:latest', 'name': 'ubuntu', 'pre_build_image': True})[0m

TASK [Create molecule instance(s)] *********************************************
[33mchanged: [localhost] => (item=instance)[0m
[33mchanged: [localhost] => (item=ubuntu)[0m

TASK [Wait for instance(s) creation to complete] *******************************
[33mchanged: [localhost] => (item={'failed': 0, 'started': 1, 'finished': 0, 'ansible_job_id': 'j179959400744.59859', 'results_file': '/root/.ansible_async/j179959400744.59859', 'changed': True, 'item': {'image': 'docker.io/pycontribs/centos:7', 'name': 'instance', 'pre_build_image': True}, 'ansible_loop_var': 'item'})[0m
[1;30mFAILED - RETRYING: [localhost]: Wait for instance(s) creation to complete (300 retries left).[0m
[33mchanged: [localhost] => (item={'failed': 0, 'started': 1, 'finished': 0, 'ansible_job_id': 'j737759247160.59893', 'results_file': '/root/.ansible_async/j737759247160.59893', 'changed': True, 'item': {'image': 'docker.io/pycontribs/ubuntu:latest', 'name': 'ubuntu', 'pre_build_image': True}, 'ansible_loop_var': 'item'})[0m

PLAY RECAP *********************************************************************
[33mlocalhost[0m                  : [32mok=6   [0m [33mchanged=2   [0m unreachable=0    failed=0    [36mskipped=5   [0m rescued=0    ignored=0

[34mINFO    [0m [2;36mRunning [0m[2;32mdefault[0m[2;36m > [0m[2;32mprepare[0m
[31mWARNING [0m Skipping, prepare playbook not configured.
[34mINFO    [0m [2;36mRunning [0m[2;32mdefault[0m[2;36m > [0m[2;32mconverge[0m

PLAY [Converge] ****************************************************************

TASK [Gathering Facts] *********************************************************
[32mok: [ubuntu][0m
[32mok: [instance][0m

TASK [Include vector-role] *****************************************************

TASK [vector-role : Vector| Install package] ***********************************
[36mincluded: /opt/jenkins_agent/workspace/freestyle molecule test/roles/vector-role/tasks/install_yum.yml for instance[0m
[36mincluded: /opt/jenkins_agent/workspace/freestyle molecule test/roles/vector-role/tasks/install_apt.yml for ubuntu[0m

TASK [vector-role : Install Vector | YUM install] ******************************
[33mchanged: [instance][0m

TASK [vector-role : Install Vector | prepare architecture name when x64] *******
[32mok: [ubuntu][0m

TASK [vector-role : Install Vector | prepare architecture name when else] ******
[36mskipping: [ubuntu][0m

TASK [vector-role : Install Vector | DEB install] ******************************
[33mchanged: [ubuntu][0m

TASK [vector-role : Deploy config Vector] **************************************
[33mchanged: [ubuntu][0m
[33mchanged: [instance][0m

TASK [vector-role : Creates directory] *****************************************
[33mchanged: [instance][0m
[33mchanged: [ubuntu][0m

TASK [vector-role : Create systemd unit Vector] ********************************
[33mchanged: [instance][0m
[33mchanged: [ubuntu][0m

RUNNING HANDLER [vector-role : restart vector service] *************************
[36mskipping: [instance][0m
[36mskipping: [ubuntu][0m

PLAY RECAP *********************************************************************
[33minstance[0m                   : [32mok=6   [0m [33mchanged=4   [0m unreachable=0    failed=0    [36mskipped=1   [0m rescued=0    ignored=0
[33mubuntu[0m                     : [32mok=7   [0m [33mchanged=4   [0m unreachable=0    failed=0    [36mskipped=2   [0m rescued=0    ignored=0

[34mINFO    [0m [2;36mRunning [0m[2;32mdefault[0m[2;36m > [0m[2;32midempotence[0m

PLAY [Converge] ****************************************************************

TASK [Gathering Facts] *********************************************************
[32mok: [ubuntu][0m
[32mok: [instance][0m

TASK [Include vector-role] *****************************************************

TASK [vector-role : Vector| Install package] ***********************************
[36mincluded: /opt/jenkins_agent/workspace/freestyle molecule test/roles/vector-role/tasks/install_yum.yml for instance[0m
[36mincluded: /opt/jenkins_agent/workspace/freestyle molecule test/roles/vector-role/tasks/install_apt.yml for ubuntu[0m

TASK [vector-role : Install Vector | YUM install] ******************************
[32mok: [instance][0m

TASK [vector-role : Install Vector | prepare architecture name when x64] *******
[32mok: [ubuntu][0m

TASK [vector-role : Install Vector | prepare architecture name when else] ******
[36mskipping: [ubuntu][0m

TASK [vector-role : Install Vector | DEB install] ******************************
[32mok: [ubuntu][0m

TASK [vector-role : Deploy config Vector] **************************************
[32mok: [instance][0m
[32mok: [ubuntu][0m

TASK [vector-role : Creates directory] *****************************************
[32mok: [instance][0m
[32mok: [ubuntu][0m

TASK [vector-role : Create systemd unit Vector] ********************************
[32mok: [instance][0m
[32mok: [ubuntu][0m

PLAY RECAP *********************************************************************
[32minstance[0m                   : [32mok=6   [0m changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
[32mubuntu[0m                     : [32mok=7   [0m changed=0    unreachable=0    failed=0    [36mskipped=1   [0m rescued=0    ignored=0

[34mINFO    [0m Idempotence completed successfully.
[34mINFO    [0m [2;36mRunning [0m[2;32mdefault[0m[2;36m > [0m[2;32mside_effect[0m
[31mWARNING [0m Skipping, side effect playbook not configured.
[34mINFO    [0m [2;36mRunning [0m[2;32mdefault[0m[2;36m > [0m[2;32mverify[0m
[34mINFO    [0m Running Ansible Verifier

PLAY [Verify] ******************************************************************

TASK [Example assertion] *******************************************************
[32mok: [instance] => {[0m
[32m    "changed": false,[0m
[32m    "msg": "All assertions passed"[0m
[32m}[0m
[32mok: [ubuntu] => {[0m
[32m    "changed": false,[0m
[32m    "msg": "All assertions passed"[0m
[32m}[0m

TASK [Check vector config] *****************************************************
[32mok: [instance] => {[0m
[32m    "changed": false,[0m
[32m    "msg": "All assertions passed"[0m
[32m}[0m
[32mok: [ubuntu] => {[0m
[32m    "changed": false,[0m
[32m    "msg": "All assertions passed"[0m
[32m}[0m

PLAY RECAP *********************************************************************
[32minstance[0m                   : [32mok=2   [0m changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
[32mubuntu[0m                     : [32mok=2   [0m changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

[34mINFO    [0m Verifier completed successfully.
[34mINFO    [0m [2;36mRunning [0m[2;32mdefault[0m[2;36m > [0m[2;32mcleanup[0m
[31mWARNING [0m Skipping, cleanup playbook not configured.
[34mINFO    [0m [2;36mRunning [0m[2;32mdefault[0m[2;36m > [0m[2;32mdestroy[0m

PLAY [Destroy] *****************************************************************

TASK [Set async_dir for HOME env] **********************************************
[32mok: [localhost][0m

TASK [Destroy molecule instance(s)] ********************************************
[33mchanged: [localhost] => (item=instance)[0m
[33mchanged: [localhost] => (item=ubuntu)[0m

TASK [Wait for instance(s) deletion to complete] *******************************
[33mchanged: [localhost] => (item=instance)[0m
[33mchanged: [localhost] => (item=ubuntu)[0m

TASK [Delete docker networks(s)] ***********************************************
[36mskipping: [localhost][0m

PLAY RECAP *********************************************************************
[33mlocalhost[0m                  : [32mok=3   [0m [33mchanged=2   [0m unreachable=0    failed=0    [36mskipped=1   [0m rescued=0    ignored=0

[34mINFO    [0m Pruning extra files from scenario ephemeral directory
Finished: SUCCESS`
2. Сделать Declarative Pipeline Job, который будет запускать `molecule test` из любого вашего репозитория с ролью.
3. Перенести Declarative Pipeline в репозиторий в файл `Jenkinsfile`.
4. Создать Multibranch Pipeline на запуск `Jenkinsfile` из репозитория.
5. Создать Scripted Pipeline, наполнить его скриптом из [pipeline](./pipeline).
6. Внести необходимые изменения, чтобы Pipeline запускал `ansible-playbook` без флагов `--check --diff`, если не установлен параметр при запуске джобы (prod_run = True). По умолчанию параметр имеет значение False и запускает прогон с флагами `--check --diff`.
7. Проверить работоспособность, исправить ошибки, исправленный Pipeline вложить в репозиторий в файл `ScriptedJenkinsfile`.
8. Отправить ссылку на репозиторий с ролью и Declarative Pipeline и Scripted Pipeline.

## Необязательная часть

1. Создать скрипт на groovy, который будет собирать все Job, завершившиеся хотя бы раз неуспешно. Добавить скрипт в репозиторий с решением и названием `AllJobFailure.groovy`.
2. Создать Scripted Pipeline так, чтобы он мог сначала запустить через Yandex Cloud CLI необходимое количество инстансов, прописать их в инвентори плейбука и после этого запускать плейбук. Мы должны при нажатии кнопки получить готовую к использованию систему.

---

### Как оформить решение задания

Выполненное домашнее задание пришлите в виде ссылки на .md-файл в вашем репозитории.

---
