#Software #Hacking #WebExplotation #Computación 
# Definición
A group of underground hackers might be using this legit site to communicate. Use your forensic techniques to uncover their messageTry it [here](http://standard-pizzas.picoctf.net:59512/)!
# Hints
- In the country that doesn't exist, the flag persists
# Solución
Primero vemos la página, y la inspeccionamos.
```bash
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>flags are stepic</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <h1>Country Flags</h1>
    <div class="flag-grid" id="flag-grid">
      
    </div>

    <script>
        const flags = [
        { name: "Afghanistan",img: "flags/af.png"},
        { name: "Åland Islands",img: "flags/ax.png"},
        { name: "Albania",img: "flags/al.png"},
        { name: "Algeria",img: "flags/dz.png"},
        { name: "American Samoa",img: "flags/as.png"},
        { name: "Andorra",img: "flags/ad.png"},
        { name: "Angola",img: "flags/ao.png"},
        { name: "Anguilla",img: "flags/ai.png"},
        { name: "Antarctica [b]",img: "flags/aq.png"},
        { name: "Antigua and Barbuda",img: "flags/ag.png"},
        { name: "Argentina",img: "flags/ar.png"},
        { name: "Armenia",img: "flags/am.png"},
        { name: "Aruba",img: "flags/aw.png"},
        { name: "Australia [c]",img: "flags/au.png"},
        { name: "Austria",img: "flags/at.png"},
        { name: "Azerbaijan",img: "flags/az.png"},
        { name: "Bahamas (the)",img: "flags/bs.png"},
        { name: "Bahrain",img: "flags/bh.png"},
        { name: "Bangladesh",img: "flags/bd.png"},
        { name: "Barbados",img: "flags/bb.png"},
        { name: "Belarus",img: "flags/by.png"},
        { name: "Belgium",img: "flags/be.png"},
        { name: "Belize",img: "flags/bz.png"},
        { name: "Benin",img: "flags/bj.png"},
        { name: "Bermuda",img: "flags/bm.png"},
        { name: "Bhutan",img: "flags/bt.png"},
        { name: "Bolivia (Plurinational State of)",img: "flags/bo.png"},
        { name: "Bonaire  Sint Eustatius Saba",img: "flags/bq.png"},
        { name: "Bosnia and Herzegovina",img: "flags/ba.png"},
        { name: "Botswana",img: "flags/bw.png"},
        { name: "Brazil",img: "flags/br.png"},
        { name: "British Indian Ocean Territory (the)",img: "flags/io.png"},
        { name: "Brunei Darussalam [f]",img: "flags/bn.png"},
        { name: "Bulgaria",img: "flags/bg.png"},
        { name: "Burkina Faso",img: "flags/bf.png"},
        { name: "Burundi",img: "flags/bi.png"},
        { name: "Cabo Verde [g]",img: "flags/cv.png"},
        { name: "Cambodia",img: "flags/kh.png"},
        { name: "Cameroon",img: "flags/cm.png"},
        { name: "Canada",img: "flags/ca.png"},
        { name: "Cayman Islands (the)",img: "flags/ky.png"},
        { name: "Central African Republic (the)",img: "flags/cf.png"},
        { name: "Chad",img: "flags/td.png"},
        { name: "Chile",img: "flags/cl.png"},
        { name: "China",img: "flags/cn.png"},
        { name: "Christmas Island",img: "flags/cx.png"},
        { name: "Cocos (Keeling) Islands (the)",img: "flags/cc.png"},
        { name: "Colombia",img: "flags/co.png"},
        { name: "Comoros (the)",img: "flags/km.png"},
        { name: "Congo (the Democratic Republic of the)",img: "flags/cd.png"},
        { name: "Congo (the) [h]",img: "flags/cg.png"},
        { name: "Cook Islands (the)",img: "flags/ck.png"},
        { name: "Costa Rica",img: "flags/cr.png"},
        { name: "Côte d'Ivoire [i]",img: "flags/ci.png"},
        { name: "Croatia",img: "flags/hr.png"},
        { name: "Cuba",img: "flags/cu.png"},
        { name: "Curaçao",img: "flags/cw.png"},
        { name: "Cyprus",img: "flags/cy.png"},
        { name: "Czechia [j]",img: "flags/cz.png"},
        { name: "Denmark",img: "flags/dk.png"},
        { name: "Djibouti",img: "flags/dj.png"},
        { name: "Dominica",img: "flags/dm.png"},
        { name: "Dominican Republic (the)",img: "flags/do.png"},
        { name: "Ecuador",img: "flags/ec.png"},
        { name: "Egypt",img: "flags/eg.png"},
        { name: "El Salvador",img: "flags/sv.png"},
        { name: "Equatorial Guinea",img: "flags/gq.png"},
        { name: "Eritrea",img: "flags/er.png"},
        { name: "Estonia",img: "flags/ee.png"},
        { name: "Eswatini [k]",img: "flags/sz.png"},
        { name: "Ethiopia",img: "flags/et.png"},
        { name: "Falkland Islands (the) [Malvinas] [l]",img: "flags/fk.png"},
        { name: "Faroe Islands (the)",img: "flags/fo.png"},
        { name: "Fiji",img: "flags/fj.png"},
        { name: "Finland",img: "flags/fi.png"},
        { name: "France [m]",img: "flags/fr.png"},
        { name: "French Guiana",img: "flags/gf.png"},
        { name: "French Polynesia",img: "flags/pf.png"},
        { name: "French Southern Territories (the) [n]",img: "flags/tf.png"},
        { name: "Gabon",img: "flags/ga.png"},
        { name: "Gambia (the)",img: "flags/gm.png"},
        { name: "Georgia",img: "flags/ge.png"},
        { name: "Germany",img: "flags/de.png"},
        { name: "Ghana",img: "flags/gh.png"},
        { name: "Gibraltar",img: "flags/gi.png"},
        { name: "Greece",img: "flags/gr.png"},
        { name: "Greenland",img: "flags/gl.png"},
        { name: "Grenada",img: "flags/gd.png"},
        { name: "Guadeloupe",img: "flags/gp.png"},
        { name: "Guam",img: "flags/gu.png"},
        { name: "Guatemala",img: "flags/gt.png"},
        { name: "Guernsey",img: "flags/gg.png"},
        { name: "Guinea",img: "flags/gn.png"},
        { name: "Guinea-Bissau",img: "flags/gw.png"},
        { name: "Guyana",img: "flags/gy.png"},
        { name: "Haiti",img: "flags/ht.png"},
        { name: "Heard Island and McDonald Islands",img: "flags/hm.png"},
        { name: "Holy See (the) [o]",img: "flags/va.png"},
        { name: "Honduras",img: "flags/hn.png"},
        { name: "Hong Kong",img: "flags/hk.png"},
        { name: "Hungary",img: "flags/hu.png"},
        { name: "Iceland",img: "flags/is.png"},
        { name: "India",img: "flags/in.png"},
        { name: "Indonesia",img: "flags/id.png"},
        { name: "Iran (Islamic Republic of)",img: "flags/ir.png"},
        { name: "Iraq",img: "flags/iq.png"},
        { name: "Ireland",img: "flags/ie.png"},
        { name: "Isle of Man",img: "flags/im.png"},
        { name: "Israel",img: "flags/il.png"},
        { name: "Italy",img: "flags/it.png"},
        { name: "Jamaica",img: "flags/jm.png"},
        { name: "Japan",img: "flags/jp.png"},
        { name: "Jersey",img: "flags/je.png"},
        { name: "Jordan",img: "flags/jo.png"},
        { name: "Kazakhstan",img: "flags/kz.png"},
        { name: "Kenya",img: "flags/ke.png"},
        { name: "Kiribati",img: "flags/ki.png"},
        { name: "Korea (the Democratic People's Republic of) [p]",img: "flags/kp.png"},
        { name: "Korea (the Republic of) [q]",img: "flags/kr.png"},
        { name: "Kuwait",img: "flags/kw.png"},
        { name: "Kyrgyzstan",img: "flags/kg.png"},
        { name: "Lao People's Democratic Republic (the) [r]",img: "flags/la.png"},
        { name: "Latvia",img: "flags/lv.png"},
        { name: "Lebanon",img: "flags/lb.png"},
        { name: "Lesotho",img: "flags/ls.png"},
        { name: "Liberia",img: "flags/lr.png"},
        { name: "Libya",img: "flags/ly.png"},
        { name: "Liechtenstein",img: "flags/li.png"},
        { name: "Lithuania",img: "flags/lt.png"},
        { name: "Luxembourg",img: "flags/lu.png"},
        { name: "Macao [s]",img: "flags/mo.png"},
        { name: "Madagascar",img: "flags/mg.png"},
        { name: "Malawi",img: "flags/mw.png"},
        { name: "Malaysia",img: "flags/my.png"},
        { name: "Maldives",img: "flags/mv.png"},
        { name: "Mali",img: "flags/ml.png"},
        { name: "Malta",img: "flags/mt.png"},
        { name: "Marshall Islands (the)",img: "flags/mh.png"},
        { name: "Martinique",img: "flags/mq.png"},
        { name: "Mauritania",img: "flags/mr.png"},
        { name: "Mauritius",img: "flags/mu.png"},
        { name: "Mayotte",img: "flags/yt.png"},
        { name: "Mexico",img: "flags/mx.png"},
        { name: "Micronesia (Federated States of)",img: "flags/fm.png"},
        { name: "Moldova (the Republic of)",img: "flags/md.png"},
        { name: "Monaco",img: "flags/mc.png"},
        { name: "Mongolia",img: "flags/mn.png"},
        { name: "Montenegro",img: "flags/me.png"},
        { name: "Montserrat",img: "flags/ms.png"},
        { name: "Morocco",img: "flags/ma.png"},
        { name: "Mozambique",img: "flags/mz.png"},
        { name: "Myanmar [t]",img: "flags/mm.png"},
        { name: "Namibia",img: "flags/na.png"},
        { name: "Nauru",img: "flags/nr.png"},
        { name: "Nepal",img: "flags/np.png"},
        { name: "Netherlands, Kingdom of the",img: "flags/nl.png"},
        { name: "New Caledonia",img: "flags/nc.png"},
        { name: "New Zealand",img: "flags/nz.png"},
        { name: "Nicaragua",img: "flags/ni.png"},
        { name: "Niger (the)",img: "flags/ne.png"},
        { name: "Nigeria",img: "flags/ng.png"},
        { name: "Niue",img: "flags/nu.png"},
        { name: "Norfolk Island",img: "flags/nf.png"},
        { name: "North Macedonia [u]",img: "flags/mk.png"},
        { name: "Northern Mariana Islands (the)",img: "flags/mp.png"},
        { name: "Norway",img: "flags/no.png"},
        { name: "Oman",img: "flags/om.png"},
        { name: "Pakistan",img: "flags/pk.png"},
        { name: "Palau",img: "flags/pw.png"},
        { name: "Palestine, State of",img: "flags/ps.png"},
        { name: "Panama",img: "flags/pa.png"},
        { name: "Papua New Guinea",img: "flags/pg.png"},
        { name: "Paraguay",img: "flags/py.png"},
        { name: "Peru",img: "flags/pe.png"},
        { name: "Philippines (the)",img: "flags/ph.png"},
        { name: "Pitcairn [v]",img: "flags/pn.png"},
        { name: "Poland",img: "flags/pl.png"},
        { name: "Portugal",img: "flags/pt.png"},
        { name: "Puerto Rico",img: "flags/pr.png"},
        { name: "Qatar",img: "flags/qa.png"},
        { name: "Réunion",img: "flags/re.png"},
        { name: "Romania",img: "flags/ro.png"},
        { name: "Russian Federation (the) [w]",img: "flags/ru.png"},
        { name: "Rwanda",img: "flags/rw.png"},
        { name: "Saint Barthélemy",img: "flags/bl.png"},
        { name: "Saint Helena Ascension Island Tristan da Cunha",img: "flags/sh.png"},
        { name: "Saint Kitts and Nevis",img: "flags/kn.png"},
        { name: "Saint Lucia",img: "flags/lc.png"},
        { name: "Saint Martin (French part)",img: "flags/mf.png"},
        { name: "Saint Pierre and Miquelon",img: "flags/pm.png"},
        { name: "Saint Vincent and the Grenadines",img: "flags/vc.png"},
        { name: "Samoa",img: "flags/ws.png"},
        { name: "San Marino",img: "flags/sm.png"},
        { name: "Sao Tome and Principe",img: "flags/st.png"},
        { name: "Saudi Arabia",img: "flags/sa.png"},
        { name: "Senegal",img: "flags/sn.png"},
        { name: "Serbia",img: "flags/rs.png"},
        { name: "Seychelles",img: "flags/sc.png"},
        { name: "Sierra Leone",img: "flags/sl.png"},
        { name: "Singapore",img: "flags/sg.png"},
        { name: "Sint Maarten (Dutch part)",img: "flags/sx.png"},
        { name: "Slovakia",img: "flags/sk.png"},
        { name: "Slovenia",img: "flags/si.png"},
        { name: "Solomon Islands",img: "flags/sb.png"},
        { name: "Somalia",img: "flags/so.png"},
        { name: "South Africa",img: "flags/za.png"},
        { name: "South Georgia and the South Sandwich Islands",img: "flags/gs.png"},
        { name: "South Sudan",img: "flags/ss.png"},
        { name: "Spain",img: "flags/es.png"},
        { name: "Sri Lanka",img: "flags/lk.png"},
        { name: "Sudan (the)",img: "flags/sd.png"},
        { name: "Suriname",img: "flags/sr.png"},
        { name: "Sweden",img: "flags/se.png"},
        { name: "Switzerland",img: "flags/ch.png"},
        { name: "Syrian Arab Republic (the) [y]",img: "flags/sy.png"},
        { name: "Taiwan (Province of China) [z]",img: "flags/tw.png"},
        { name: "Tajikistan",img: "flags/tj.png"},
        { name: "Tanzania, the United Republic of",img: "flags/tz.png"},
        { name: "Thailand",img: "flags/th.png"},
        { name: "Timor-Leste [ab]",img: "flags/tl.png"},
        { name: "Togo",img: "flags/tg.png"},
        { name: "Tokelau",img: "flags/tk.png"},
        { name: "Tonga",img: "flags/to.png"},
        { name: "Trinidad and Tobago",img: "flags/tt.png"},
        { name: "Tunisia",img: "flags/tn.png"},
        { name: "Türkiye [ac]",img: "flags/tr.png"},
        { name: "Turkmenistan",img: "flags/tm.png"},
        { name: "Turks and Caicos Islands (the)",img: "flags/tc.png"},
        { name: "Tuvalu",img: "flags/tv.png"},
        { name: "Uganda",img: "flags/ug.png"},
        { name: "Ukraine",img: "flags/ua.png"},
        { name: "United Arab Emirates (the)",img: "flags/ae.png"},
        { name: "United Kingdom of Great Britain and Northern Ireland (the)",img: "flags/gb.png"},
        { name: "United States of America (the)",img: "flags/us.png"},
        { name: "Upanzi, Republic The",img: "flags/upz.png", style:"width: 120px!important; height: 90px!important;" },
        { name: "Uruguay",img:"flags/uy.png"},
        { name: "Uzbekistan",img: "flags/uz.png"},
        { name: "Vanuatu",img: "flags/vu.png"},
        { name: "Venezuela (Bolivarian Republic of)",img: "flags/ve.png"},
        { name: "Viet Nam [ag]",img: "flags/vn.png"},
        { name: "Virgin Islands (British) [ah]",img: "flags/vg.png"},
        { name: "Virgin Islands (U.S.) [ai]",img: "flags/vi.png"},
        { name: "Wallis and Futuna",img: "flags/wf.png"},
        { name: "Yemen",img: "flags/ye.png"},
        { name: "Zambia",img: "flags/zm.png"},
        { name: "Zimbabwe",img: "flags/zw.png"},
        ];
        const flagGrid = document.getElementById('flag-grid');
        flags.forEach(flag => {
            const flagItem = document.createElement('div');
            flagItem.className = 'flag-item';
            const flagImg = document.createElement('img');
            flagImg.src = flag.img;
            flagImg.alt = `${[flag.name](http://flag.name/)} Flag`;
            const flagName = document.createElement('span');
            flagName.textContent = [flag.name](http://flag.name/);
            flagItem.appendChild(flagImg);
            flagItem.appendChild(flagName);
            flagGrid.appendChild(flagItem);
        });
    </script>
</body>
</html>  
```
  
Siguiendo la pista, buscamos el país falso en la lista, apoyándonos de [deepseek](https://chat.deepseek.com/). Y vemos que es el siguiente:
name: "Upanzi, Republic The",img: "flags/upz.png", style:"width: 120px!important; height: 90px!important;"  

Vemos que su imagen esta contenida en "flags/upz.png", por lo que usando [[wget]] obtenemos la imagen.
```bash
┌──(kali㉿kali)-[~/fla]  
└─$ wget [http://standard-pizzas.picoctf.net:55384/flags/upz.png](http://standard-pizzas.picoctf.net:55384/flags/upz.png)  
--2025-05-10 19:10:54--  [http://standard-pizzas.picoctf.net:55384/flags/upz.png](http://standard-pizzas.picoctf.net:55384/flags/upz.png)  
Resolving [standard-pizzas.picoctf.net](http://standard-pizzas.picoctf.net/) ([standard-pizzas.picoctf.net](http://standard-pizzas.picoctf.net/))... 3.22.195.189  
Connecting to [standard-pizzas.picoctf.net](http://standard-pizzas.picoctf.net/) ([standard-pizzas.picoctf.net](http://standard-pizzas.picoctf.net/))|3.22.195.189|:55384... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 1788400 (1.7M) [image/png]  
Saving to: ‘upz.png’  
  
upz.png             100%[================>]   1.71M   388KB/s    in 5.5s      
  
2025-05-10 19:11:04 (320 KB/s) - ‘upz.png’ saved [1788400/1788400]  
                                                                        
┌──(kali㉿kali)-[~/fla]  
└─$ file upz.png       
upz.png: PNG image data, 14173 x 10630, 8-bit/color RGBA, non-interlaced  
```
                                                                               
Finalmente usamos [[Stepic]] (como el nombre del problema -asegurándonos que este instalado-) para ver información oculta en esta imagen.
```bash
┌──(kali㉿kali)-[~/fla]  
└─$ sudo apt install stepic     
[sudo] password for kali:   
The following packages were automatically installed and are no longer required:  
  libflac12t64   libglapi-mesa         ruby-zeitwerk  
  libgeos3.13.0  python3-setproctitle  
Use 'sudo apt autoremove' to remove them.  
  
Installing:  
  stepic  
                                                                               
Summary:  
  Upgrading: 0, Installing: 1, Removing: 0, Not Upgrading: 0  
  Download size: 10.1 kB  
  Space needed: 50.2 kB / 60.0 GB available  
  
Get:1 [http://kali.download/kali](http://kali.download/kali) kali-rolling/main amd64 stepic all 0.5.0-2 [10.1 kB]  
Fetched 10.1 kB in 6s (1,759 B/s)    
Selecting previously unselected package stepic.  
(Reading database ... 413599 files and directories currently installed.)  
Preparing to unpack .../stepic_0.5.0-2_all.deb ...  
Unpacking stepic (0.5.0-2) ...  
Setting up stepic (0.5.0-2) ...  
Processing triggers for doc-base (0.11.2) ...  
Processing 1 added doc-base file...  
Processing triggers for man-db (2.13.0-1) ...  
Processing triggers for kali-menu (2025.1.1) ...  
                                                                               
┌──(kali㉿kali)-[~/fla]  
└─$ stepic -d -i upz.png     
/usr/lib/python3/dist-packages/PIL/Image.py:3402: DecompressionBombWarning: Image size (150658990 pixels) exceeds limit of 89478485 pixels, could be decompression bomb DOS attack.  
  warnings.warn(  
picoCTF{fl4g_h45_fl4g3e22f365}
```
Y obtenemos la bandera.
## Respuesta
picoCTF{fl4g_h45_fl4g3e22f365}