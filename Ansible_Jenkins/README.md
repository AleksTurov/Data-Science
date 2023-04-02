Установка и настройка Jenkins через Ansible
Данный скрипт позволяет установить и запустить Jenkins на ВМ1 с помощью Ansible.

Шаги для выполнения скрипта
Убедитесь, что на целевой машине (ВМ1) установлена операционная система, поддерживаемая Jenkins.
Установите Ansible на управляющую машину.
Создайте инвентарный файл Ansible (например, inventory.ini), в котором укажите адреса хостов, которые будут управляться с помощью Ansible.
Создайте плейбук Ansible (например, jenkins.yml) со следующим содержимым:
- name: Install and configure Jenkins
  hosts: server1
  become: true

  tasks:
    - name: Update yum cache and upgrade packages
      yum:
        name: '*'
        state: latest
      become: true

    - name: Install Java
      yum:
        name: java-1.8.0-openjdk-devel
        state: present
      become: true

    - name: Add Jenkins repository key
      rpm_key:
        key: https://pkg.jenkins.io/redhat-stable/jenkins.io.key
        state: present
      become: true

    - name: Add Jenkins repository
      yum_repository:
        name: jenkins
        description: Jenkins-stable
        baseurl: http://pkg.jenkins.io/redhat-stable/
        gpgcheck: yes
        gpgkey: https://pkg.jenkins.io/redhat-stable/jenkins.io.key
      become: true

    - name: Install Jenkins
      yum:
        name: jenkins
        state: present
      become: true

    - name: Start and enable Jenkins service
      systemd:
        name: jenkins
        state: started
        enabled: yes
      become: true

Запустите плейбук с помощью команды:

ansible-playbook -i inventory.ini jenkins.yml

После успешного выполнения плейбука, Jenkins будет установлен и запущен на ВМ1. Перейдите на веб-интерфейс Jenkins, чтобы продолжить его настройку.
Обратите внимание, что данный скрипт был создан на основе предположения, что управляющая машина и ВМ1 используют RedHat-подобную операционную систему. Если у вас другая операционная система, то скрипт может потребовать некоторых изменений.
