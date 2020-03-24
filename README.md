<h1>ANSIBLE PLAYBOOK FOR CENTOS 8 AND KOHA 19.11</h1> 
<h3>(based on https://github.com/nemobis/beic-koha)</h3>

<ol>
  <li>Install Core CentOS 8 – Choose Server software package, Connect to Network, set hostname, set time zone, make partitions as needed, set root password and create Admin user (koha-admin) </li>
  <li>Update CentOS – sudo yum update</li>
  <li>Enable EPEL – sudo yum -y install epel-release</li>
  <li>Update Install – sudo yum -y update</li>
  <li>Install MariaDB - sudo yum install mariadb*</li>
  <li>Install Perl – sudo yum install perl</li>
  <li>Install Ansible, Git, cpanminus - sudo yum -y install ansible git cpanminus</li>
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

