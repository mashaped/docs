# Features of sending and receiving messages to numbers of different countries

??? question "Russian Federation telephone numbers"

    All Russian numbers must have country code 7, if you specify 8 in the code number, messages sent via API will be sent to a non-existent account, you can check the correctness of the number using the request https://wa.me/80123456789. As a result, the phone number will include 11 digits: +7 XXX XXX XXXX.

    > If you enter the number in the phone book 80123456789, WhatsApp will automatically transfer to the existing account 70123456789.
    > The checkWhatsapp method will return "existsWhatsapp": true.

    > Required number to send messages 70123456789@c.us
    
??? question "Mexican telephone numbers"

    In all Mexican numbers, the number "1" must be inserted between the country code "52" and the area code (also for the Nextel operator). The code "11" at the beginning must be removed. As a result, the phone number will include 13 digits: +52 1 XXX XXX XXXX.

    > Original phone number +520123456789
    >
    > Required number to send messages 5210123456789@c.us


??? question "Argentina telephone numbers"

    In all Argentine telephone numbers, the number 9 must be inserted between the country code "54" and the area code. The code "15" at the beginning must be removed. As a result, the phone number will include 13 digits: +54 9 XXX XXX XXXX.

    > Original phone number +540123456789
    >
    > Required number to send messages 5490123456789@c.us
 

??? question "Brazil telephone numbers"

    In some regions of Brazil, the digit 9 has been added to the phone number, between the local phone number and the Brazilian area code. List of area codes to which you need to add the number 9: 11-19, 21, 22, 24, 27, 28. For Brazilian numbers with other area codes, you need to remove the number 9.

    As a result, the phone number can include 12 or 13 digits +55 21 (9) XXXX XXXX,
    where 55 is the country code, 21 is the region code, XXXX XXXX is the local phone number.

    > Original phone number +552112345678
    >
    > Required number to send messages 5521912345678@c.us

    ??? success "Python code example"
        
        Install the package
        ```
        pip install phonenumbers
        ```

        ```python
        import phonenumbers
        # is the only areas that whatspp updated for 9h digit
        UPDATED_AREA_CODE = {"55": ["11", "12", "13", "14", "15", "16", "17", "18", "19", "21", "22", "24", "27", "28"]}

        def prepare_whatsapp_number(phone):

            x = phonenumbers.parse(phone, None)
            country_code = str(x.country_code)
            area_code = str(x.national_number)[0:2]
            
            phone = phone.replace('+','')
            
            updated_area = UPDATED_AREA_CODE
            
            if updated_area.get(country_code):
                area_code_updated = updated_area[country_code]  

                # Remove or add the 9h digit for states that were not updated 
                if area_code not in area_code_updated:
                    if len(str(x.national_number)) == 11:
                        phone = '%s%s%s' % (country_code, area_code, str(x.national_number)[3:])
                else:
                    if len(str(x.national_number)) == 10:
                        phone = '%s%s%s%s' % (country_code, area_code,"9", str(x.national_number)[2:])
            
            return phone

        print(prepare_whatsapp_number("+559212345678"))
        print(prepare_whatsapp_number("+5592912345678")) #phone number not working
        ```

    Information taken from [article](https://support.gupshup.io/hc/en/articles/4407840924953-A-brief-note-on-the-inconsistencies-for-mobile-numbers-and-their-WhatsApp-IDs-in-Brazil-digit-9-Mexico-digit-1-)