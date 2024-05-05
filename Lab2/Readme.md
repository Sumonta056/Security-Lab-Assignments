### 📝 Lab 2: Attacking Classic Crypto Systems

#### ✅ Checkpoint – 1 : Caesar Cipher

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

#### ✅ Checkpoint – 2 : A Substitution Cipher

![alt text](./Checkpoint%20-%202/image.png)

- Write a program to decipher each of them that has been created using a substitution cipher.

```c++


```

- Input - 1 Cipher Text :

```text
Cipher-1: af p xpkcaqvnpk pfg, af ipqe qpri, gauuikifc tpw, ceiri udvk tiki afgarxifrphni cd eao--wvmd popkwn, hiqpvri du ear jvaql vfgikrcpfgafm du cei xkafqaxnir du xrwqedearcdkw pfg du ear aopmafpcasi xkdhafmr afcd fit pkipr. ac tpr qdoudkcafm cd lfdt cepc au pfwceafm epxxifig cd ringdf eaorinu hiudki cei opceiopcaqr du cei uaing qdvng hi qdoxnicinw tdklig dvc--pfg edt rndtnw ac xkdqiigig, pfg edt odvfcpafdvr cei dhrcpqnir--ceiki tdvng pc niprc kiopaf dfi
mddg oafg cepc tdvng qdfcafvi cei kiripkq
```

- Output Code :

```
---------
i    46    11.33
d    36    8.867
c    33    8.12808
p    32    7.88177
a    31    7.63547
f    30    7.38916
r    23    5.66502
e    22    5.41872
g    19    4.6798
k    19    4.6798
n    16    3.94089
q    15    3.69458
v    13    3.20197
u    13    3.20197
t    11    2.70936
o    11    2.70936
x    10    2.46305
w    8    1.97044
m    7    1.72414
h    6    1.47783
l    3    0.738916
s    1    0.246305
j    1    0.246305
z    0    0
y    0    0
b    0    0
---------
IN A PARTICULAR AND, IN EACH CASE, DIFFERENT WAY, THESE FOUR WERE INDISPENSABLE TO HIMYUGO AMARYL, BECAUSE OF HIS QUICK UNDERSTANDING OF THE PRINCIPLES OF PSYCHOHISTORY AND OF HIS IMAGINATIVE PROBINGS INTO NEW AREAS. IT WAS COMFORTING TO KNOW THAT IF ANYTHING HAPPENED TO SELDON HIMSELF BEFORE THE MATHEMATICS OF THE FIELD COULD BE COMPLETELY WORKED OUTAND HOW SLOWLY IT PROCEEDED, AND HOW MOUNTAINOUS THE OBSTACLESTHERE WOULD AT LEAST REMAIN ONE GOOD MIND THAT WOULD CONTINUE THE RESEARCH
```

<hr>

- Input - 2 Cipher Text :

```text
Cipher-2: aceah toz puvg vcdl omj puvg yudqecov, omj loj auum klu thmjuv hs klu zlcvu shv zcbkg guovz, upuv zcmdu lcz vuwovroaeu jczoyyuovomdu omj qmubyudkuj vukqvm. klu
vcdluz lu loj avhqnlk aodr svhw lcz kvopuez loj mht audhwu o ehdoe eunumj, omj ck toz
yhyqeoveg auecupuj, tlokupuv klu hej sher wcnlk zog, klok klu lcee ok aon umj toz sqee hs kqmmuez zkqssuj tckl kvuozqvu. omj cs klok toz mhk umhqnl shv sowu, kluvu toz oezh lcz yvhehmnuj pcnhqv kh wovpue ok. kcwu thvu hm, aqk ck zuuwuj kh lopu eckkeu ussudk hm wv. aonncmz. ok mcmukg lu toz wqdl klu zowu oz ok scskg. ok mcmukg-mcmu klug aunom kh doee lcw tuee-yvuzuvpuj; aqk qmdlomnuj thqej lopu auum muovuv klu wovr. kluvu tuvu zhwu klok zlhhr klucv luojz omj klhqnlk klcz toz khh wqdl hs o nhhj klcmn; ck zuuwuj qmsocv klok omghmu zlhqej yhzzuzz (oyyovumkeg) yuvyukqoe ghqkl oz tuee oz (vuyqkujeg) cmubloqzkcaeu tuoekl. ck tcee lopu kh au yocj shv, klug zocj. ck czm'k mokqvoe, omj kvhqaeu tcee dhwu hs ck! aqk zh sov kvhqaeu loj mhk dhwu; omj oz wv. aonncmz toz numuvhqz tckl lcz whmug, whzk yuhyeu tuvu tceecmn kh shvncpu lcw lcz hjjckcuz omj lcz nhhj shvkqmu. lu vuwocmuj hm pczckcmn kuvwz tckl lcz vueokcpuz (ubduyk, hs dhqvzu, klu zodrpceeuaonncmzuz), omj lu loj womg juphkuj ojwcvuvz owhmn klu lhaackz hs yhhv omj qmcwyhvkomk sowcecuz. aqk lu loj mh dehzu svcumjz, qmkce zhwu hs lcz ghqmnuv dhqzcmz aunom kh nvht qy. klu uejuzk hs kluzu, omj aceah'z sophqvcku, toz ghqmn svhjh aonncmz. tlum aceah toz mcmukg-mcmu lu ojhykuj svhjh oz lcz lucv, omj avhqnlk lcw kh ecpu ok aon umj; omj klu lhyuz hs klu zodrpceeu- aonncmzuz tuvu scmoeeg jozluj. aceah omj svhjh loyyumuj kh lopu klu zowu acvkljog, zuykuwauv 22mj. ghq loj aukkuv dhwu omj ecpu luvu, svhjh wg eoj, zocj aceah hmu jog; omj klum tu dom dueuavoku hqv acvkljog-yovkcuz dhwshvkoaeg khnukluv. ok klok kcwu svhjh toz zkcee cm lcz ktuumz, oz klu lhaackz doeeuj klu cvvuzyhmzcaeu ktumkcuz auktuum dlcejlhhj omj dhwcmn hs onu ok klcvkg-klvuu
```
