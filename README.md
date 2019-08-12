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
  
  
  


