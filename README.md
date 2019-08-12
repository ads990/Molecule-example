# Molecule

From the docs:

*Molecule is designed to aid in the development and testing of Ansible roles.*
*Molecule provides support for testing with multiple instances, operating systems and distributions, virtualization providers, test frameworks and testing scenarios.*
*Molecule encourages an approach that results in consistently developed roles that are well-written, easily understood and maintained.*


**Source documentation:**
https://molecule.readthedocs.io/en/stable/index.html


**What in the repo:**
- Vagrant config file (uses CentOS)
- Playbook to configure above VM with Molecule (and all prereqs including docker as Molecule's test environment)
- This README with Molecule overview

**What Molecule can test against a role**

- **Yaml syntax:** this will be done using configured lintel and can be configured as desired. It will help with common Yaml syntax errors and/or adherence to best practices
  
- **Execution of a role against different platforms:** this will ensure that role can be successfully used on different OS/version (e.g. RHEL6 or 7 or 8). It will require preparation of adequate environments to exercute tests against.
  
- **Execution of a role using different version of Ansible engine:** it will help with regression testing when upgrading Ansible
  
- **Role idempotence:** this will ensure that Ansible code is developed correctly and repeated execution isn't trigerring repeated actions (or in other words, follow up runs don't make any changes to a target system).
  
- **Functional test of a role:** this is the essence of the testing - making sure that expected configuration state is reached. 
  
  
**And how this is done?**

Molecule is a python module. Once it is installed on a host it can be 'invoked' by 'molecule' command. All options and details available in quoted online documentation, but to provide some overview, quick look at how testing is performed:
- molecule can either initialize a new role or work withing an existing one
- molecule will work with 'scenarios'. Scenario will be described by files located inside a role folder, in 'molecule' subfolder. Each scenario will present a separate test case, where each will be executed after another in sequence. For example first scenario might be testing a role against CentOS7 and Ansible2.5, second will repeat but with Ansible2.7, third would do the same but against RHEL8 and so on.
- molecule scenario will configure test steps, providers and environment - for example, whether to run a test inside a docker container or a VMWare WVM, what linter (syntax checker) to use (if any), whether idempotence test is to be run, and finally what verifier to use (which also can be configured)
- each separate test can be invoked separately (e.g. run just syntax check)

**Example from this repo**

Prerequisites:
1. Vagrant with VirtualBox
2. Access to internet

Steps:
1. Clone the repo to your local host with Vagrant


