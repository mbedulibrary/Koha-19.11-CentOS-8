<h1>ANSIBLE PLAYBOOK FOR CENTOS 8 AND KOHA 19.11</h1> 
<h3>(based on https://github.com/nemobis/beic-koha)</h3>

<ol>
  <li>Install Core CentOS 8 – Choose Server software package and select Basic Web in right column, Connect to Network, set time zone, make partitions as needed, set root password and create Admin user (koha-admin) </li>
  <li>Update CentOS – sudo dnf update</li>
  <li>Enable EPEL Repo – sudo dnf -y install epel-release</li>
  <li>Enable PowerTools Repo – sudo dnf config-manager --set-enabled PowerTools</li>
  <li>Update Install – sudo dnf -y update</li>
  <li>Install apache – sudo dnf install httpd
    <ul>
      <li>
        If local network access needed :<br>
        # firewall-cmd --zone=public --permanent --add-service=http<br>
        # firewall-cmd --reload
      </li>
     </ul>
  </li>
  <li>Install Ansible - sudo dnf -y install ansible</li>
  <li>Create user koha, group koha and add koha (user) to koha and apache groups
    <ul>
      <li>sudo adduser koha</li>
      <li>sudo usermod -a -G koha koha</li>
      <li>sudo usermod -a -G apache koha</li>
    </ul>
  <li>Clone or Download ansible playbook</li>
  <li>Go to Download Location of ansible playbook</li>
  <li>Run Ansible - sudo ansible-playbook koha.yml –u koha –i inventory.ini --connection local</li>
  <li>Secure MySQL Database - sudo mysql_secure_installation</li>
  <li>Open port for Staff Client - sudo firewall-cmd --zone=public --permanent --add-port 8080/tcp</li>
  <li>Find IP address of install server or localhost on port 8080 (localhost:8080) and begin web installation (username: kohaadmin password:katikoan)</li>
  <li>Go to About Koha and update required Perl modules manually with cpanm (ex:sudo cpanm Module::Name)</li>
  <li>Start and enable memcached at boot:
    <ul>
      <li>sudo systemctl start memcached</li>
      <li>sudo systemctl enable memcached</li>
    </ul>
  </li>
</ol>
# koha-ansible-V2
# koha-ansible-v2

