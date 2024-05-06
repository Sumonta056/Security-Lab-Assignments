# 📝 Lab 2: Attacking Classic Crypto Systems

## ✅ Checkpoint – 1 : Caesar Cipher

- **Writing a program to decipher a text has been created using the Caesar cipher.**

```python
# Define the alphabets that we will use for the Caesar cipher
alphabet = "abcdefghijklmnopqrstuvwxyz"

def decrypt_caesar_cipher(ciphertext, key):
    # Initialize the plaintext as an empty string
    plaintext = ""

    # Loop over each character in the ciphertext
    for char in ciphertext:
        # Convert the character to lowercase
        char = char.lower()

        # If the character is not in the alphabet, add it to the plaintext as is
        if char not in alphabet:
            plaintext += char
        else:
            # Find the index of the character in the alphabet
            index = alphabet.find(char)

            # Subtract the key from the index to decrypt
            new_index = index - key

            # If the new index is negative, wrap around to the end of the alphabet
            if new_index < 0:
                new_index += 26

            # Add the decrypted character to the plaintext
            plaintext += alphabet[new_index]

    # Return the decrypted text
    return plaintext

# Define the ciphertext and key
ciphertext = "odroboewscdrolocdcwkbdmyxdbkmdzvkdpybwyeddrobo"
key = 1

# Decrypt the ciphertext and print the result
print(decrypt_caesar_cipher(ciphertext, key))

# Decrypt the ciphertext and print the result for all key 1- 16
with open('output.txt', 'w') as f:
    for k in range(1,26):
        decrypted_text = decrypt_caesar_cipher(ciphertext,k)
        f.write(f"key: {k} decrypted_text: {decrypted_text}\n\n")
```

- Output Code :

```text
key: 1 decrypted_text: ncqnandvrbcqnknbcbvjaclxwcajlcyujcoxavxdccqnan
key: 2 decrypted_text: mbpmzmcuqabpmjmabauizbkwvbzikbxtibnwzuwcbbpmzm
key: 3 decrypted_text: laolylbtpzaolilzazthyajvuayhjawshamvytvbaaolyl
key: 4 decrypted_text: kznkxkasoyznkhkyzysgxziutzxgizvrgzluxsuazznkxk
key: 5 decrypted_text: jymjwjzrnxymjgjxyxrfwyhtsywfhyuqfyktwrtzyymjwj
key: 6 decrypted_text: ixliviyqmwxlifiwxwqevxgsrxvegxtpexjsvqsyxxlivi
key: 7 decrypted_text: hwkhuhxplvwkhehvwvpduwfrqwudfwsodwiruprxwwkhuh
key: 8 decrypted_text: gvjgtgwokuvjgdguvuoctveqpvtcevrncvhqtoqwvvjgtg
key: 9 decrypted_text: fuifsfvnjtuifcftutnbsudpousbduqmbugpsnpvuuifsf
key: 10 decrypted_text: ethereumisthebestsmartcontractplatformoutthere
key: 11 decrypted_text: dsgdqdtlhrsgdadrsrlzqsbnmsqzbsokzsenqlntssgdqd
key: 12 decrypted_text: crfcpcskgqrfczcqrqkypramlrpyarnjyrdmpkmsrrfcpc
key: 13 decrypted_text: bqebobrjfpqebybpqpjxoqzlkqoxzqmixqclojlrqqebob
key: 14 decrypted_text: apdanaqieopdaxaopoiwnpykjpnwyplhwpbknikqppdana
key: 15 decrypted_text: zoczmzphdnoczwznonhvmoxjiomvxokgvoajmhjpooczmz
key: 16 decrypted_text: ynbylyogcmnbyvymnmgulnwihnluwnjfunzilgionnbyly
key: 17 decrypted_text: xmaxkxnfblmaxuxlmlftkmvhgmktvmietmyhkfhnmmaxkx
key: 18 decrypted_text: wlzwjwmeaklzwtwklkesjlugfljsulhdslxgjegmllzwjw
key: 19 decrypted_text: vkyvivldzjkyvsvjkjdriktfekirtkgcrkwfidflkkyviv
key: 20 decrypted_text: ujxuhukcyijxuruijicqhjsedjhqsjfbqjvehcekjjxuhu
key: 21 decrypted_text: tiwtgtjbxhiwtqthihbpgirdcigprieapiudgbdjiiwtgt
key: 22 decrypted_text: shvsfsiawghvspsghgaofhqcbhfoqhdzohtcfacihhvsfs
key: 23 decrypted_text: rgurerhzvfgurorfgfznegpbagenpgcyngsbezbhggurer
key: 24 decrypted_text: qftqdqgyueftqnqefeymdfoazfdmofbxmfradyagfftqdq
key: 25 decrypted_text: pespcpfxtdespmpdedxlcenzyeclneawleqzcxzfeespcp
```

- Here We Can see that the `key 10` is the correct key for the given ciphertext.

```
key: 10 decrypted_text: ethereumisthebestsmartcontractplatformoutthere
```

<hr>

## ✅ Checkpoint – 2 : A Substitution Cipher

![alt text](./Checkpoint%20-%202/image.png)

- Writing a program to decipher each of the text that has been created using a substitution cipher.

```python
from collections import namedtuple
from operator import attrgetter

CharFreq = namedtuple('CharFreq', 'ch cnt per')

def char_substitution(prev, cur, message):
    return message.replace(prev, cur)

def main():
    with open('cipher.txt', 'r') as f:
        cipher = f.read().strip()

    n = len(cipher)

    frequency = [0]*27
    cnt = 0
    for i in range(n):
        if 'a' <= cipher[i] <= 'z':
            idx = ord(cipher[i]) - ord('a')
            frequency[idx] += 1
            cnt += 1

    y = float(cnt)

    char_frequency = []
    for i in range(26):
        ch = chr(ord('a') + i)
        x = float(frequency[i])
        per = (x / y) * 100.0
        char_frequency.append(CharFreq(ch, frequency[i], per))

    print("---------")
    char_frequency.sort(key=attrgetter('per'), reverse=True)
    for i in range(26):
        ch = char_frequency[i].ch
        freq = char_frequency[i].cnt
        per = char_frequency[i].per

        print(ch, freq, per)

    print("---------")
    message = cipher

    with open('substitutions.txt', 'r') as f:
        substitutions = [tuple(line.strip().split()) for line in f]

    for prev, cur in substitutions:
        message = char_substitution(prev, cur, message)

    print(message)

if __name__ == "__main__":
    main()
```

- **Input - 1 (Cipher Text) :**

Cipher-1: af p xpkcaqvnpk pfg, af ipqe qpri, gauuikifc tpw, ceiri udvk tiki afgarxifrphni cd eao--wvmd popkwn, hiqpvri du ear jvaql vfgikrcpfgafm du cei xkafqaxnir du xrwqedearcdkw pfg du ear aopmafpcasi xkdhafmr afcd fit pkipr. ac tpr qdoudkcafm cd lfdt cepc au pfwceafm epxxifig cd ringdf eaorinu hiudki cei opceiopcaqr du cei uaing qdvng hi qdoxnicinw tdklig dvc--pfg edt rndtnw ac xkdqiigig, pfg edt odvfcpafdvr cei dhrcpqnir--ceiki tdvng pc niprc kiopaf dfi mddg oafg cepc tdvng qdfcafvi cei kiripkq

- Input - 1 : Substitution Mapping Table:

```text
a I
c T
d O
e H
f N
g D
h B
i E
j Q
k R
l K
m G
n L
o M
p A
q C
r S
s V
t W
u F
w Y
x P
v U
```

- Output Code :

```
---------
i 46 11.358024691358025
d 36 8.88888888888889
c 33 8.148148148148149
p 32 7.901234567901234
a 31 7.654320987654321
f 30 7.4074074074074066
r 23 5.679012345679013
e 21 5.185185185185185
g 19 4.691358024691358
k 19 4.691358024691358
n 16 3.950617283950617
q 15 3.7037037037037033
u 13 3.2098765432098766
v 13 3.2098765432098766
o 11 2.7160493827160495
t 11 2.7160493827160495
x 10 2.4691358024691357
w 8 1.9753086419753085
m 7 1.728395061728395
h 6 1.4814814814814816
l 3 0.7407407407407408
j 1 0.24691358024691357
s 1 0.24691358024691357
b 0 0.0
y 0 0.0
z 0 0.0
---------
```

- **Dicipher Text Output**

IN A PARTICULAR AND, IN EACH CASE, DIFFERENT WAY, THESE FOUR WERE INDISPENSABLE TO HIMYUGO AMARYL, BECAUSE OF HIS QUICK UNDERSTANDING OF THE PRINCIPLES OF PSYCHOHISTORY AND OF HIS IMAGINATIVE PROBINGS INTO NEW AREAS. IT WAS COMFORTING TO KNOW THAT IF ANYTHING HAPPENED TO SELDON HIMSELF BEFORE THE MATHEMATICS OF THE FIELD COULD BE COMPLETELY WORKED OUTAND HOW SLOWLY IT PROCEEDED, AND HOW MOUNTAINOUS THE OBSTACLESTHERE WOULD AT LEAST REMAIN ONE GOOD MIND THAT WOULD CONTINUE THE RESEARCH

<hr>

- **Input - 2 (Cipher Text) :**

Cipher-2: aceah toz puvg vcdl omj puvg yudqecov, omj loj auum klu thmjuv hs klu zlcvu shv zcbkg guovz, upuv zcmdu lcz vuwovroaeu jczoyyuovomdu omj qmubyudkuj vukqvm. klu
vcdluz lu loj avhqnlk aodr svhw lcz kvopuez loj mht audhwu o ehdoe eunumj, omj ck toz
yhyqeoveg auecupuj, tlokupuv klu hej sher wcnlk zog, klok klu lcee ok aon umj toz sqee hs kqmmuez zkqssuj tckl kvuozqvu. omj cs klok toz mhk umhqnl shv sowu, kluvu toz oezh lcz yvhehmnuj pcnhqv kh wovpue ok. kcwu thvu hm, aqk ck zuuwuj kh lopu eckkeu ussudk hm wv. aonncmz. ok mcmukg lu toz wqdl klu zowu oz ok scskg. ok mcmukg-mcmu klug aunom kh doee lcw tuee-yvuzuvpuj; aqk qmdlomnuj thqej lopu auum muovuv klu wovr. kluvu tuvu zhwu klok zlhhr klucv luojz omj klhqnlk klcz toz khh wqdl hs o nhhj klcmn; ck zuuwuj qmsocv klok omghmu zlhqej yhzzuzz (oyyovumkeg) yuvyukqoe ghqkl oz tuee oz (vuyqkujeg) cmubloqzkcaeu tuoekl. ck tcee lopu kh au yocj shv, klug zocj. ck czm'k mokqvoe, omj kvhqaeu tcee dhwu hs ck! aqk zh sov kvhqaeu loj mhk dhwu; omj oz wv. aonncmz toz numuvhqz tckl lcz whmug, whzk yuhyeu tuvu tceecmn kh shvncpu lcw lcz hjjckcuz omj lcz nhhj shvkqmu. lu vuwocmuj hm pczckcmn kuvwz tckl lcz vueokcpuz (ubduyk, hs dhqvzu, klu zodrpceeuaonncmzuz), omj lu loj womg juphkuj ojwcvuvz owhmn klu lhaackz hs yhhv omj qmcwyhvkomk sowcecuz. aqk lu loj mh dehzu svcumjz, qmkce zhwu hs lcz ghqmnuv dhqzcmz aunom kh nvht qy. klu uejuzk hs kluzu, omj aceah'z sophqvcku, toz ghqmn svhjh aonncmz. tlum aceah toz mcmukg-mcmu lu ojhykuj svhjh oz lcz lucv, omj avhqnlk lcw kh ecpu ok aon umj; omj klu lhyuz hs klu zodrpceeu- aonncmzuz tuvu scmoeeg jozluj. aceah omj svhjh loyyumuj kh lopu klu zowu acvkljog, zuykuwauv 22mj. ghq loj aukkuv dhwu omj ecpu luvu, svhjh wg eoj, zocj aceah hmu jog; omj klum tu dom dueuavoku hqv acvkljog-yovkcuz dhwshvkoaeg khnukluv. ok klok kcwu svhjh toz zkcee cm lcz ktuumz, oz klu lhaackz doeeuj klu cvvuzyhmzcaeu ktumkcuz auktuum dlcejlhhj omj dhwcmn hs onu ok klcvkg-klvuu

- Input - 2 : Substitution Mapping Table:

```text
a B
b X
c I
d C
e L
g Y
h O
j D
k T
l H
m N
n G
o A
p V
q U
r K
s F
t W
u E
v R
w M
z S
y P
```

- Output Code :

```
---------
u 113 12.098501070663811
h 77 8.244111349036402
k 76 8.137044967880087
o 74 7.922912205567452
c 70 7.494646680942184
z 63 6.745182012847965
m 59 6.316916488222699
l 53 5.674518201284797
j 49 5.2462526766595285
v 47 5.032119914346895
e 44 4.710920770877944
a 33 3.5331905781584587
n 23 2.462526766595289
q 23 2.462526766595289
w 22 2.355460385438972
s 21 2.2483940042826553
y 20 2.141327623126338
t 19 2.0342612419700217
g 18 1.9271948608137044
d 15 1.6059957173447537
p 11 1.177730192719486
b 2 0.21413276231263384
r 2 0.21413276231263384
f 0 0.0
i 0 0.0
x 0 0.0
---------
```

- **Dicipher Text Output**

BILBO WAS VERY RICH AND VERY PECULIAR, AND HAD BEEN THE WONDER OF THE SHIRE FOR SIXTY YEARS, EVER SINCE HIS REMARKABLE DISAPPEARANCE AND UNEXPECTED RETURN. THE RICHES HE HAD BROUGHT BACK FROM HIS TRAVELS HAD NOW BECOME A LOCAL LEGEND, AND IT WAS POPULARLY BELIEVED, WHATEVER THE OLD FOLK MIGHT SAY, THAT THE HILL AT BAG END WAS FULL OF TUNNELS STUFFED WITH TREASURE. AND IF THAT WAS NOT ENOUGH FOR FAME, THERE WAS ALSO HIS PROLONGED VIGOUR TO MARVEL AT. TIME WORE ON, BUT IT SEEMED TO HAVE LITTLE EFFECT ON MR. BAGGINS. AT NINETY HE WAS MUCH THE SAME AS AT FIFTY. AT NINETY-NINE THEY BEGAN TO CALL HIM WELL-PRESERVED; BUT UNCHANGED WOULD HAVE BEEN NEARER THE MARK. THERE WERE SOME THAT SHOOK THEIR HEADS AND THOUGHT THIS WAS TOO MUCH OF A GOOD THING; IT SEEMED UNFAIR THAT ANYONE SHOULD POSSESS (APPARENTLY) PERPETUAL YOUTH AS WELL AS (REPUTEDLY) INEXHAUSTIBLE WEALTH. IT WILL HAVE TO BE PAID FOR, THEY SAID. IT ISN'T NATURAL, AND TROUBLE WILL COME OF IT! BUT SO FAR TROUBLE HAD NOT COME; AND AS MR. BAGGINS WAS GENEROUS WITH HIS MONEY, MOST PEOPLE WERE WILLING TO FORGIVE HIM HIS ODDITIES AND HIS GOOD FORTUNE. HE REMAINED ON VISITING TERMS WITH HIS RELATIVES (EXCEPT, OF COURSE, THE SACKVILLEï¿½BAGGINSES), AND HE HAD MANY DEVOTED ADMIRERS AMONG THE HOBBITS OF POOR AND UNIMPORTANT FAMILIES. BUT HE HAD NO CLOSE FRIENDS, UNTIL SOME OF HIS YOUNGER COUSINS BEGAN TO GROW UP. THE ELDEST OF THESE, AND BILBO'S FAVOURITE, WAS YOUNG FRODO BAGGINS. WHEN BILBO WAS NINETY-NINE HE ADOPTED FRODO AS HIS HEIR, AND BROUGHT HIM TO LIVE AT BAG END; AND THE HOPES OF THE SACKVILLE- BAGGINSES WERE FINALLY DASHED. BILBO AND FRODO HAPPENED TO HAVE THE SAME BIRTHDAY, SEPTEMBER 22ND. YOU HAD BETTER COME AND LIVE HERE, FRODO MY LAD, SAID BILBO ONE DAY; AND THEN WE CAN CELEBRATE OUR BIRTHDAY-PARTIES COMFORTABLY TOGETHER. AT THAT TIME FRODO WAS STILL IN HIS TWEENS, AS THE HOBBITS CALLED THE IRRESPONSIBLE TWENTIES BETWEEN CHILDHOOD AND COMING OF AGE AT THIRTY-THREE

<hr>

#### ❓ Question : Which input was easier to break? Explain why.

- The Input - 2 was easier to break because the frequency of the characters in the cipher text was more evenly distributed. The frequency of the characters in the cipher text of Input - 1 was more skewed, which made it harder to break.