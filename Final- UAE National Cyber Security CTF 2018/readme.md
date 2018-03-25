Hello CTFs Players!
I'm GeneralEG from N3WB135_T34M

Today i will explain how to solve the web challenges of CyberTalents UAE Final Round. 

-BTW my teammate Khaled explained how to solve the web challenges of CyberTalents EGYPT Final Round Here:
http://khaledibnalwalid.com/final-cybertalents-2018-ctf-writeup/

Well! 
let's start... 




# The First Challenge 
# Easy Message  (50pts)

in index.php
you will find a login page
so let's go to robots.txt
and Ooh $hit :

User-agent: *
Disallow: /?source

then let's go to /?source

Woooot!! :D Amazing!

if ($user == base64_decode('Q3liZXItVGFsZW50') && $pass == base64_decode('Q3liZXItVGFsZW50')

Let's decode base64.. tool:
https://codebeautify.org/base64-decode

... Done! 
username and password=Cyber-Talent

Logged in! 
let's see what is going on! 

I Have a Message For You


..-. .-.. .- --. -.--. .. -....- -.- -. ----- .-- -....- -.-- ----- ..- -....- .- .-. ...-- -....- -- ----- .-. ... ...-- -.--.-
    


Cool it's DOT DOT HASH "Morse"
let's decode it! tool:
https://morsecode.scphillips.com/translator.html

Nice! 

FLAG<KN>I-KN0W-Y0U-AR3-M0RS3)

Link:
http://ec2-35-164-4-176.us-west-2.compute.amazonaws.com/easymessage/





# The Second Challenge : 
# Big Number (100pts)

Well, 
what we have here! 
it's a login page needs a password. 
let's click in source to get the source! 

Good!! 

    if (isset($_GET['password'])) {
    if (is_numeric($_GET['password'])){
        if (strlen($_GET['password']) < 4){
            if ($_GET['password'] > 999)
                die($flag);

so we need a number
 less than 4 digits 
greater than 999 
WTF! it's Weird Math LOL! 
But wait!!! 
we know that PHP also understand hexadecimal  :D

so let's convert decimal to hexadecimal
tool:
https://www.binaryhexconverter.com/decimal-to-hex-converter
results:
 1000 = 3E8
Cool! it's less than 4 digits and greater than 999 :D

Let's login with our new password and Done! 

FLAG{Yes_Y0u_C4n_Use_Exp0nentiaL}

Link:
http://ec2-35-164-4-176.us-west-2.compute.amazonaws.com/bignumber/




# The Third Challenge : 
# Owls Blog (100pts)

Well,
We have a weird blog here! 
with error:
Undefined index: search in /var/www/html/owls/index.php on line 12

cool we got the name of our page and our parameter! 
index.php?search=


Let's check the robots.txt 

Cool! 
User-agent: *
Disallow: git.phps

Let's download this file and open it! 

$search = $POST['search'];
if (!preg_match('/^-?[0-9a-z]+$/m', $POST["search"])) {
  

Interesting filter! with preg_match :D

so let's ask for help in Google ❤️
Gotcha!!! this function is vulnerable :"D

we can bypass it with \n let's encode it 
%0a
We are ready now to pwn it! 

The Final Payload:
A%0a%27 UNION SELECT flag FROM flag #

Ooh Yeah! Done. 

 Flag{R3G3X_Ar3_NOT_GOOD_For_OW3ls}

Link:
view-source:ec2-35-164-4-176.us-west-2.compute.amazonaws.com/owls/

-----
<h1> Finally all thanks for my team ( Ahmed ezzat , Khaled Ibn Al-Walid , Naseem Abdellatef ) . </h1>

<h1> Cheers, </h1> 
<h1> GeneralEG </h1> 
