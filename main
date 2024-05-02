import ipaddress

def range_to_subnet(ip_start, ip_end,subnets=[]):
    if ip_start>=ip_end:
        return []
    if ip_end%2 == 1:
        return range_to_subnet(ip_start,ip_end+1,subnets)
    if ip_start%2 ==1:
        subnets.append(f"{ipaddress.IPv4Address(ip_start)}/32")
        return range_to_subnet(ip_start+1,ip_end,subnets)
    ip_range = ip_end - ip_start
    print(ip_range)
    max_subnet = math.floor(math.log2(ip_range))
    subnet_size = 32
    for subnet_size in range((32-max_subnet),32):
        print(subnet_size,2**(32-subnet_size), ip_start % 2**(32-subnet_size))
        if ip_start % 2**(32-subnet_size) == 0:
            break
    # print int to xxx.xxx.xxx.xxx/xx format using ipaddress module
    if subnet_size == 32:
        return
    if ip_start + 2**(32-subnet_size) < ip_end:
        range_to_subnet(ip_start + 2**(32-subnet_size),ip_end,subnets)            
    subnets.append(f"{ipaddress.IPv4Address(ip_start)}/{subnet_size}")
    print(ipaddress.IPv4Address(ip_start),subnet_size)
    return subnets

ip_start = "10.117.0.1"
ip_end = "192.168.1.32"

start_int = int(ipaddress.IPv4Address(ip_start))
end_int = int(ipaddress.IPv4Address(ip_end))
subnets = []

print(range_to_subnet(start_int,end_int,subnets))
