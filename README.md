# learning


#!/bin/bash

echo "=== System Information ==="
echo "OS Version: $(cat /etc/os-release | grep PRETTY_NAME | cut -d= -f2 | tr -d '\"')"
echo "Kernel Version: $(uname -r)"
echo "Uptime: $(uptime -p)"
echo "CPU Cores: $(nproc)"
echo "Memory Info:"
free -h
echo "Swap Info:"
swapon --show
echo "Cache Memory:"
grep -i '^Cached:' /proc/meminfo

echo "=== Increasing ulimit ==="
ulimit -n 1028
echo "New ulimit (open files): $(ulimit -n)"

echo "=== Changing Time Zone to Brussels ==="
timedatectl set-timezone Europe/Brussels
echo "Current Timezone: $(timedatectl | grep 'Time zone')"






#!/bin/bash

read -sp "Enter your password: " password
echo

# Check conditions
length_check=false
alpha_num_check=false
case_check=false

# Minimum 10 characters
[[ ${#password} -ge 10 ]] && length_check=true

# At least one letter and one number
[[ $password =~ [A-Za-z] && $password =~ [0-9] ]] && alpha_num_check=true

# At least one lowercase and one uppercase
[[ $password =~ [a-z] && $password =~ [A-Z] ]] && case_check=true

if $length_check && $alpha_num_check && $case_check; then
    echo "Strong Password"
else
    echo "Weak Password"
fi








#!/bin/bash

# Create directory q4
mkdir q4
cd q4

# Create subdirectories
mkdir dir1 dir2 dir3 dir4

# Create files
touch file1.txt file1.js file2.txt file2.ts file4.py file5.tf file2.md file.md file.sh file.yml

#Return to the original directory
cd ..
