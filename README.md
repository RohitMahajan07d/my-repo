def Dec_Bin(num): 
    ans = 0  
    mul = 1  
    while num: 
        rem = num % 2 
        num = num // 2 
        ans = ans + rem * mul   
        mul = mul * 10 
    return ans 
 
def Bin_Dec(num): 
    ans = 0  
    mul = 1  
    while num: 
        rem = num % 10 
        num = num // 10 
        ans = ans + rem * mul   
        mul = mul * 2 
    return ans 
 
print("Choose an option:\n1. Decimal to Binary\n2. Binary to Decimal")   
choice = input("Enter your choice (1 or 2): ") 
 
match choice: 
    case '1': 
        ip_address = input("Enter Decimal IP address (e.g. 192.168.1.1): ") 
        part1, part2, part3, part4 = ip_address.split('.') 
        part1, part2, part3, part4 = int(part1), int(part2), int(part3), int(part4) 
 
        b1 = Dec_Bin(part1) 
        b2 = Dec_Bin(part2) 
        b3 = Dec_Bin(part3) 
        b4 = Dec_Bin(part4) 
 
        result = f"{b1}.{b2}.{b3}.{b4}" 
        print("Binary IP Address:", result) 
 
    case '2': 
        ip_address = input("Enter Binary IP address (e.g. 11000000.10101000.1.1): ") 
        part1, part2, part3, part4 = ip_address.split('.') 
        part1, part2, part3, part4 = int(part1), int(part2), int(part3), int(part4) 
 
        d1 = Bin_Dec(part1) 
        d2 = Bin_Dec(part2) 
        d3 = Bin_Dec(part3) 
        d4 = Bin_Dec(part4) 
 
        result = f"{d1}.{d2}.{d3}.{d4}" 
        print("Decimal IP Address:", result) 
 
    case _: 
        print("Invalid choice. (Enter only either 1 or 2)")
