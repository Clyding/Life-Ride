# Life Ride
 Emergency Suicide Prevention App
 acc_e = list()
acc_num = list()
acc_pw = list()
acc_name = list()
acc_gen = list()
acc_add = list()
acc_zip = list()
acc_rid_num = list()
acc_pref_rid_gen = list()
# account = acc_name + acc_gen + acc_e + acc_num + acc_add + acc_pw + acc_rid_num + acc_pref_rid_gen
def main():
    log_in = int(input('1. Log in\n2. Sign up\n'))
    if log_in == 1:
        create(log_in, acc_e)
    else:
        sign_up()

def create(log_in, acc_e):
    if log_in == 1:
        email = input('Enter your email address: ')
        if email in acc_e:
            password = input("Enter your password: ")

            
        else:
            print('Account not found')
            sign_up()

def sign_up():
    # file = open('hackathon.txt', 'r')
    email = email_check(acc_e)
    print(acc_e)
    phone = IsPhoneNumber(acc_num)
    print(acc_num)
    passw = pass_w(acc_pw)
    print(acc_pw)
    name = get_name(acc_name)
    print(acc_name)
    gender = gender_(acc_gen)
    print(acc_gen)
    address = get_address(acc_add, acc_zip)
    print(acc_add)
    print('Here at LifeRide, we believe in a sense of community. If you need a helping hand, there should be someone there to lend it to you.\n When you press the EMERGENCY button, fellow riders are available to come to the rescue, but 3 might be a crowd for some.')
    rid_num = int(input("How many people do you want to help if you're in need? "))
    print("Everyone's personal safety is imprtant to us. We want to make sure every rider feels safe and comfortable recieving help from who ever is avaiable.")
    rid_gend = pref_gen(acc_pref_rid_gen)
    print('Sign up complete!')
    # settings(name, gender, phone, email, rid_num, rid_gend, address)
    # print(account)

def email_check(acc_e):
    email = ''
    while email == '':
        email = input('Email address: ')
        if '@' not in email:
            print('Not a valid email. Try again.')
            email = ''
            continue
        if '.com' not in email:
            if '.edu' not in email:
                if '.org' not in email:
                    print('Not a valid email. Try again.')
                    email = ''
                    continue
                
    acc_e.append(email)

def IsPhoneNumber(acc_num):
    phone = ''
    for i in range(10):
        if phone == '':
            while phone == '':
                phone = input('Phone number: ')
                if not phone[i].isdecimal():
                    print('Try again.')
                    phone = ''
                    continue
                if len(phone) != 10:
                    print('Try again.')
                    phone = ''
                    continue
                else:
                    break
        else:
            break
    acc_num.append(phone)

def pass_w(acc_pw):
    passw = input('Enter password: ')
    acc_pw.append(passw)

def get_name(acc_name):
    fname = input('First name: ')
    lname = input('Last name: ')
    name = fname + ' ' + lname
    acc_name.append(name)
    return name

def gender_(acc_gen):
    gender = int(input('What is your gender?\n1. Female\n2. Male\n3. Nonbinary\n'))
    if gender == 1:
        gender = 'Female'
    elif gender == 2:
        gender = 'Male'
    elif gender == 3:
        gender = 'Nonbinary'
    acc_gen.append(gender)
    return gender

def get_address(acc_add, acc_zip):
    print("Don't worry. Your address will only be visible if you press the emergency button. Thoough, your name will still be anonymous.")
    street = input('Enter street address: ')
    city = input('Enter city: ')
    state = input('Enter state: ')
    zip_ = input('Enter zipcode: ')
    address = street + ', ' + city +', ' + state +', ' + zip_
    acc_add.append(address)
    acc_zip.append(zip_)
    return address

def pref_gen(acc_pref_rid_gen):
    rid_gend = input("What gender do you prefer your riders to be?\n1. Male\n2. Female\n3. Doesn't matter")
    if rid_gend == 1:
        rid_gend = 'Male'
    if rid_gend == 2:
        rid_gend = 'Female'
    else:
        rid_gend = "Doesn't Matter"
    acc_pref_rid_gen.append(rid_gend)
    return rid_gend

def settings(name, gender, phone, email, rid_num, rid_gend, address):
    print('Name:', name)
    print('Gender:', gender)
    print('Phone number:', phone)
    print('Email Address:', email)
    print('Max riders:', rid_num)
    print('Preferred rider gender: ', rid_gend)
    print('Address: ', address)


main()
