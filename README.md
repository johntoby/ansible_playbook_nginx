# ansible_playbook_nginx
Ansible playbook to install and start nginx

Create the playbook and edit the file: 
vim nginx_playbook.yml 

paste the following into the playbook: 

---

- name: Install and start nginx
  hosts: all
  become: yes
  tasks:
    - name: Install nginx
      apt:
        name: nginx
        state: present
        update_cache: yes

    - name: start nginx
      service:
        name: nginx
        state: started
        enabled: yes


#end 

create your inventory.ini file to contain the IP addresses of your target machines 
Run this command to execute the playbook: 
# ansible-playbook -i inventory.ini nginx_playbook.yml 

Voila. nginx will be installed on all your target machines, the nginx service will be started, and finally enabled so it does not need to be started on boot. 

Thanks for reading! 
