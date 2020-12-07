# NAT_to_IP
Simple script to output IP addresses for NAT Rulebase for a Check Point R8X NAT Rulebase

To use the script place it on your management server and adjust the PACKAGE variable to match the policy package you would
like to get the NAT rulebase information to IP address.

## By default this script will only output the first 500 NAT rules in the NAT Rulebase.

Since the NAT policy contains many object types that may not include ip addresses (groups, roles, Domain Objects, Dynamic Objects, etc)
the output will only include the names of these object types.

For Hosts (192.168.1.1), Networks (192.168.1.0/24) and ip-ranges (192.168.1.1-192.168.1.100) 
will be output as ip's using their format as just described.

## Example csv file created: 
```
nat_rule_num, original_source_type, original_source_name, original_source_ip_info, original_destination_type, original_destination_name, original_destination_ip_info, translated_source_type, translated_source_name, translated_source_ip_info, translated_destination_type, translated_destination_name, translated_destination_ip_info
1,"host","cpxtesthost_3","192.19.192.3","CpmiAnyObject","Any","Any","host","cpxtesthost_3","192.19.192.3","Global","Original","Original"
2,"CpmiAnyObject","Any","Any","host","cpxtesthost_3","192.19.192.3","Global","Original","Original","host","cpxtesthost_3","192.19.192.3"
3,"host","cpxtesthost_10","192.19.192.10","CpmiAnyObject","Any","Any","host","cpxtesthost_10","192.19.192.10","Global","Original","Original"
4,"network","AWS-Local-vpc","10.30.0.0/16","network","AWS-Local-vpc","10.30.0.0/16","Global","Original","Original","Global","Original","Original"
5,"network","AWS-Local-vpc","10.30.0.0/16","CpmiAnyObject","Any","Any","network","AWS-Local-vpc","10.30.0.0/16","Global","Original","Original"
6,"network","CP_default_Office_Mode_addresses_pool","172.16.10.0/24","network","CP_default_Office_Mode_addresses_pool","172.16.10.0/24","Global","Original","Original","Global","Original","Original"
7,"network","CP_default_Office_Mode_addresses_pool","172.16.10.0/24","CpmiAnyObject","Any","Any","network","CP_default_Office_Mode_addresses_pool","172.16.10.0/24","Global","Original","Original"
8,"network","CP_default_Office_Mode_addresses_pool_2","172.16.11.0/24","network","CP_default_Office_Mode_addresses_pool_2","172.16.11.0/24","Global","Original","Original","Global","Original","Original"
9,"network","CP_default_Office_Mode_addresses_pool_2","172.16.11.0/24","CpmiAnyObject","Any","Any","network","CP_default_Office_Mode_addresses_pool_2","172.16.11.0/24","Global","Original","Original"
10,"network","Internal_Network","192.168.1.0/24","network","Internal_Network","192.168.1.0/24","Global","Original","Original","Global","Original","Original"
11,"network","Internal_Network","192.168.1.0/24","CpmiAnyObject","Any","Any","network","Internal_Network","192.168.1.0/24","Global","Original","Original"
12,"address-range","IP-range1","1.1.1.1-1.1.2.1","access-role","Test","Test","host","my_host_4","192.168.123.4","Global","Original","Original"
13,"group","new group 1","new group 1","network","10.0.0.0/8","10.0.0.0/8","host","my_host_6","192.168.123.6","host","my_host_1","192.168.123.1"
```

If you would like to add more information to the output simply add to the JSON jq query and adjust the output.
