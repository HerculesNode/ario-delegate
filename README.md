# ario Oto delegate işlemi. Script listede belirtilen adreslere 2dk arayla stake yapar.


## Linkler
 * [Hercules Telegram](https://t.me/HerculesNode)
 * [Hercules Twitter](https://twitter.com/Herculesnode)


- ilk olarak tools/delegate-stake.ts dosyasını açın ve 200 olarak ayarlayın dosyayı kaydedin ve ardından aşağıdaki kodları çalıştırın. 
- Kod listede kaç adres var ise hepsine tek tek stake işlemi yapar 
- 2-3 günde bir yapın

![image](https://github.com/HerculesNode/ario-delegate/assets/101635385/679ba253-8be7-4ae7-924d-3c8b397f4dcd)


## ilk olarak Nano açalım
```shell
nano ario.sh
```

## Aşağıdaki kodu açtığımız ario nano dosyasının içine yapıştırın CTRL + X + Y tuşlarıyla kaydedin
```shell
#!/bin/bash
cd /root/testnet-contract/

# Stake edilecek adreslerin listesi (örnek)
declare -a TARGETS=(
"oHl168xaaIWAi53qY8G0Y4EbwXe41Dix0LbdvcdvLvw"
"T0EdDRDngav9ovQFkgOxp5jh_ZyRF53_Mvzex-wKs4I"
"l0iODykz8poPjVJ2HlY-wrnzAHyp_0267w8oGvxECWk"
"s8u2SDPNU3ndJdzi-dIwJ6xJyjg4_O_stmWpJfnqQ_0"
"s91BsMWRi8E4Lkmx0cjzwFNxTnlKjX6ne4mJ2jdMjHE"
"zFBm5PN2a8AFoDivZ4cBOmspBiENWBdXz15rEXpGxC4"
"hqjcMZ8bEyF7VQBAIOlHRaOMTv8SX9Z_SFRwylxG0SU"
"qNPdvpt_iC1f3uRfmh5GPpwMPRNujWdddb7M9gWlkDU"
"lQ1e2TNADS1kLJy5gUTW2GS0s1po6s3GI15hHsgNKks"
"9my2TT05SwQrk8TCXmASpr3nh_DuEIKh5GicUfn4d-Q"
"KjdFZRz3XfMu2E_3KiDuqW0Ye-K70Kr2gbu8Z4S0Ts4"
"lUn5LRp-np-WVJyFLC38cAy1213Hhf5We3Cv6PSmyjs"
"YlDY5URaAmLNcg5BfqQHKl6-_tIIuHfp5oPjpaqLX6w"
"PE0gBR0wwHlNA4k4He0K3iYc-EKPqjgm7dG65T9pNiw"
"HGKM7G-HuP4nK0cLGW6OxHvJKpt48AX0Wc9M11TET1o"
"ghGftRJ6mcBSqL1g9b4DIfqs4tbD4CuDXtAZaYRSzDs"
"BAQYHfwzlL5Fd1w8-fr2Iu0DMUzbgjwV-EM9fTP1Oeg"
"cTAjCmyteUycFexytR8s8xJ8y6UhYjN6qNFTqVXny-c"
"vBDC_yCsXY9KrM4nFy_ngR2aN75F85650lJZnWH5tEU"
"3Gr4shi-MU94pPC1g3vlMPPl39gffOoZwAcJd8UBtcQ"
"1erDIhwoWtE_1kCV6Ouc4cXEWfpEY9JfMNJdI9Op0-0"
"KhX4ymYGPdOgq_5SbDBIHcPj7EI3JMW4xxp60y45zuY"
"PknxsIAYcyz0bgHOpH8W_IjDFBUYBLjvXezEDN_mze0"
"NrE-g7b_WCSTLNRwJXouBsPWxwXFtF4-lyg5a8Enq8w"
"5wseWFMo4M1BsCJ_lxIU1bbLH7vMTL-SImx_x7eeCYM"
"RuqD0_TLZ4METrEEkipMvJikb4EHT1MGAiZQwP_cOlw"
"GG8zi-bWN-S7ANPBfKIo48NVWyM_OEm3B-xJW_AuvCU"
"0HOIZX22DQ0Ln8JuYBDavFhP5_XRH8TQx5RvKGAQHFk"
"arn_Hkv7mwX1HALJktsiaYg_bXc5aBeddicvVf6pla4"
"BIa3UE0QEPRJC4HBSU252qHtA8ZOR4ClnzBq1LZQ_WU"
"lC5I5rQvGZn36DodBvWiMD_abkprE20p6GgGiZakk9Y"
)

# delegate-stake.ts dosyasının yedek kopyasını alın
cp tools/delegate-stake.ts tools/delegate-stake.ts.bak

# Adresler üzerinde döngü yap ve her biri için stake işlemini çalıştır
for TARGET in "${TARGETS[@]}"; do
  # delegate-stake.ts dosyasındaki `target` değerini güncelle
  sed -i "s/const target = '.*';/const target = '$TARGET';/" tools/delegate-stake.ts

  # Stake işlemini çalıştır
  yarn ts-node tools/delegate-stake.ts

  # Kısa bir bekleme süresi (isteğe bağlı)
  sleep 2m
done
```

## izin verelim
```shell
chmod +x ario.sh
```

## Scripti çalıştıralım
```shell
./ario.sh
```

- Aşağıdaki giib çıktı alıyorsanız işlem tamamdır. 

![image](https://github.com/HerculesNode/ario-delegate/assets/101635385/5ae19608-6e97-4979-8041-d4158b01d4f1)
