# Ansible_Playbook_1

Ansible playbook for running a set of commands on CISCO devices using IOS module and send output over mail.

Key Components Used in this Playbook - 
1. cisco.ios.ios_command: This module sends arbitrary commands to an IOS node and returns the results. The register keyword captures this output for later use.
2. stdout array: Each command's output is stored in the stdout list. stdout[0] contains the result of the first command, stdout[1] the second, and so on.
3. community.general.mail: This module is used to send the email via an SMTP server.
4. delegate_to: localhost: This is critical; it ensures the email is sent from your Ansible control node (which has internet/mail access) rather than attempting to send it from the Cisco device itself.
5. Collection Installation: Ensure you have the required collections by running:
`ansible-galaxy collection install cisco.ios community.general`.
6. Connection: The playbook requires `ansible_network_os=cisco.ios.ios` and appropriate SSH credentials defined in our inventory or group_vars.

