#Software #Hacking #Principiante
# Definición
Someone's commits seems to be preventing the program from working. Who is it?You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/159/challenge.zip)
# Hints
- In collaborative projects, many users can make many changes. How can you see the changes within one file?
- Read the chapter on [[ic/comunes/software/programación/Git]] from the picoPrimer [here](https://primer.picoctf.org/#_git_version_control).
- You can use `python3 <file>.py` to try running the code, though you won't need to for this challenge.
# Solución
Descargamos ([[wget]]) y descomprimimos el archivo.

```bash
AsumomezaC-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c_titan/159/challenge.zip
--2025-02-28 01:44:19--  https://artifacts.picoctf.net/c_titan/159/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.128, 3.160.22.92, 3.160.22.43, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.128|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 293915 (287K) [application/octet-stream]
Saving to: 'challenge.zip'

challenge.zip              100%[=======================================>] 287.03K  --.-KB/s    in 0.1s    

2025-02-28 01:44:19 (1.91 MB/s) - 'challenge.zip' saved [293915/293915]

AsumomezaC-picoctf@webshell:~$ unzip challenge.zip 
Archive:  challenge.zip
   creating: drop-in/
 extracting: drop-in/message.py      
   creating: drop-in/.git/
   creating: drop-in/.git/branches/
  inflating: drop-in/.git/description  
   creating: drop-in/.git/hooks/
  inflating: drop-in/.git/hooks/applypatch-msg.sample  
  inflating: drop-in/.git/hooks/commit-msg.sample  
  inflating: drop-in/.git/hooks/fsmonitor-watchman.sample  
  inflating: drop-in/.git/hooks/post-update.sample  
  inflating: drop-in/.git/hooks/pre-applypatch.sample  
  inflating: drop-in/.git/hooks/pre-commit.sample  
  inflating: drop-in/.git/hooks/pre-merge-commit.sample  
  inflating: drop-in/.git/hooks/pre-push.sample  
  inflating: drop-in/.git/hooks/pre-rebase.sample  
  inflating: drop-in/.git/hooks/pre-receive.sample  
  inflating: drop-in/.git/hooks/prepare-commit-msg.sample  
  inflating: drop-in/.git/hooks/update.sample  
   creating: drop-in/.git/info/
  inflating: drop-in/.git/info/exclude  
   creating: drop-in/.git/refs/
   creating: drop-in/.git/refs/heads/
  inflating: drop-in/.git/refs/heads/master  
   creating: drop-in/.git/refs/tags/
 extracting: drop-in/.git/HEAD       
  inflating: drop-in/.git/config     
   creating: drop-in/.git/objects/
   creating: drop-in/.git/objects/pack/
   creating: drop-in/.git/objects/info/
   creating: drop-in/.git/objects/7d/
 extracting: drop-in/.git/objects/7d/f869a15e76c28afb609fa4dbc059144ad70161  
 extracting: drop-in/.git/objects/7d/079dfdf3c26d5c2616b063dce5561b83aff592  
   creating: drop-in/.git/objects/a5/
 extracting: drop-in/.git/objects/a5/6b2529881119591fce34630170f5630f4b096c  
 extracting: drop-in/.git/objects/a5/4937354c03175e42cf68408dc707424789e7e8  
 extracting: drop-in/.git/objects/a5/2c113f73a8a49dd53b6f6a4c0128eefaa0f55a  
 extracting: drop-in/.git/objects/a5/2ee42a8debaa5d6a51aa2cde4b0581a2811e4b  
   creating: drop-in/.git/objects/3c/
 extracting: drop-in/.git/objects/3c/e5c692e2f9682a866c59ac1aeae38d35d19771  
 extracting: drop-in/.git/objects/3c/6d36ec49d233e2d4aeeffe69c335b5dd2ebe16  
 extracting: drop-in/.git/objects/3c/1a15dc4a8dff1c5dfc40f5e3597fe7c7cdbe58  
   creating: drop-in/.git/objects/32/
 extracting: drop-in/.git/objects/32/6544a21bf75fa38f486891c58119c236a7dbbf  
 extracting: drop-in/.git/objects/32/4bcf885b5cf03cedea87611f7db57105f81935  
 extracting: drop-in/.git/objects/32/4549f3a7dc10e090ec48749d4d47808f96f395  
 extracting: drop-in/.git/objects/32/e2d2ece5592b14af5b03d391bdac9a99cb9fab  
 extracting: drop-in/.git/objects/32/4f922472995e02f3f2e10b8fd9fd7f37c01c3c  
 extracting: drop-in/.git/objects/32/557fcd3e09bff7d3c656fda7f6e61e95af8dc7  
   creating: drop-in/.git/objects/28/
 extracting: drop-in/.git/objects/28/9871add646b411282a84ff33f37abfd976ca59  
 extracting: drop-in/.git/objects/28/118b77f273b8f7404b965fff30ab5616fdd6cc  
 extracting: drop-in/.git/objects/28/3cf9a86a5bf4d3bd655141150e2d48b4b71706  
   creating: drop-in/.git/objects/23/
 extracting: drop-in/.git/objects/23/e9d4ce78b3cea725992a0ce6f5eea0bf0bcdd4  
 extracting: drop-in/.git/objects/23/00153fea771536f660327e68c28f22376f186f  
 extracting: drop-in/.git/objects/23/4d3b57b4f4498621f511f3f9e9898b89efb323  
   creating: drop-in/.git/objects/80/
 extracting: drop-in/.git/objects/80/f6ecce9660dbab8e7c6e703a5dddd8fb7291ab  
 extracting: drop-in/.git/objects/80/0ed92bc8e914d8cec5380c46a9d2bd56669fa4  
 extracting: drop-in/.git/objects/80/32acd63b9bbb2ba62845e97bd171e6efb6901a  
 extracting: drop-in/.git/objects/80/41d3655681f513cd8e186009a53306f65537c6  
   creating: drop-in/.git/objects/6f/
 extracting: drop-in/.git/objects/6f/87558699ac6965a2075fa9f7359d5fcaa1f8e5  
 extracting: drop-in/.git/objects/6f/7223fbcab24f50eef2a011d8cb763ef4798a66  
 extracting: drop-in/.git/objects/6f/074b047cab66753b81097f19382ecfb662296d  
 extracting: drop-in/.git/objects/6f/3c9763b95565cff7b0d7935ae71d069f57ac14  
   creating: drop-in/.git/objects/2c/
 extracting: drop-in/.git/objects/2c/b08370dfdf24508d8dc75273b3cd1ac3dea1c7  
 extracting: drop-in/.git/objects/2c/278c7fc9555d9ebd8ee876a450dd3e1be2db3c  
 extracting: drop-in/.git/objects/2c/8dd8f8fb876ec302b243ea89bd5a7038d18b22  
 extracting: drop-in/.git/objects/2c/7d50087a558dd17eb7374c42e22cf98735b06e  
   creating: drop-in/.git/objects/20/
 extracting: drop-in/.git/objects/20/4e89d33bc3bed0d7c41d64a05674b47408ab75  
 extracting: drop-in/.git/objects/20/14e0469ad680121fc73e4be3cb291743455f10  
   creating: drop-in/.git/objects/24/
 extracting: drop-in/.git/objects/24/a763c577bd24e5e866b42c72946f9d6529f5a9  
 extracting: drop-in/.git/objects/24/083c5aac52d1400e8b26c70b6deb38e184f85a  
 extracting: drop-in/.git/objects/24/b69f92e91b975b5848649109baaa86c19153f8  
   creating: drop-in/.git/objects/1f/
 extracting: drop-in/.git/objects/1f/8288cf2f9768e5f91242ff9e199906fcf73e86  
 extracting: drop-in/.git/objects/1f/fdbbf9f51a5d1f1dffa4ecd57e9e3954404e48  
 extracting: drop-in/.git/objects/1f/9f43db878631488893d497ec2055d79d90a94c  
   creating: drop-in/.git/objects/ab/
 extracting: drop-in/.git/objects/ab/6dab9cfd223520fcfb73ea5d9dc625e182a9ca  
 extracting: drop-in/.git/objects/ab/6b7edefba3d33c0dc44c0db2f3c6ca88fa03ca  
 extracting: drop-in/.git/objects/ab/de61dbe9c36a40cbcc8fb22f650e5fcfb63b5d  
   creating: drop-in/.git/objects/d6/
 extracting: drop-in/.git/objects/d6/4f120f6b1fcc54ee41544496f15298255a215b  
 extracting: drop-in/.git/objects/d6/effc0d884845c408dea2341b171fc0c3d5e5f6  
 extracting: drop-in/.git/objects/d6/f43a16faa79efc76c18024b182b87f60acb96e  
   creating: drop-in/.git/objects/d4/
 extracting: drop-in/.git/objects/d4/efef4be6317e8195f313eb1c62724206a3d94a  
 extracting: drop-in/.git/objects/d4/88ba65de7384c7d446965fd6a33a51bd2e1e6e  
 extracting: drop-in/.git/objects/d4/f0187caefe5d5569a9fe2e1be92d33aeced5f8  
   creating: drop-in/.git/objects/e3/
 extracting: drop-in/.git/objects/e3/92c29ff023873a24b957269f378cf6929102df  
   creating: drop-in/.git/objects/25/
 extracting: drop-in/.git/objects/25/4358bb5b3a4c5909e3b6f28036c05997f2909e  
 extracting: drop-in/.git/objects/25/9e1b2a16e81693b23a531dd9d7cfd7db8ba3f0  
   creating: drop-in/.git/objects/0b/
 extracting: drop-in/.git/objects/0b/3371c4e9955ec82b385725b1fe648a92833df5  
 extracting: drop-in/.git/objects/0b/beb164025c7b48ec3349ea04aed7c12bda1f9a  
   creating: drop-in/.git/objects/52/
 extracting: drop-in/.git/objects/52/4d5eaad1da3fe514c540e4c54e947b980f679e  
 extracting: drop-in/.git/objects/52/04d597c14ae6f8d3929fd72c11f29a885006e2  
 extracting: drop-in/.git/objects/52/63681391190f09592f722aefa960165d796b91  
 extracting: drop-in/.git/objects/52/e94246f69b1777d0b611d50acc4632479e003a  
   creating: drop-in/.git/objects/e5/
 extracting: drop-in/.git/objects/e5/509837382a1634afe82f12f5a937c31171e1bc  
 extracting: drop-in/.git/objects/e5/508175efd503c7c7a0134f1c4cebbede8f796d  
 extracting: drop-in/.git/objects/e5/5662a5413bfeb6d39d86b36ff78dfd73b45978  
   creating: drop-in/.git/objects/37/
 extracting: drop-in/.git/objects/37/1982b7eb0484eb8ae873269d61c233197bff58  
 extracting: drop-in/.git/objects/37/32cfb2352ce4adee6e0b2547581ae5fa35e1d4  
 extracting: drop-in/.git/objects/37/3ae987c7cfb5e729803a8f7c989cbc685584c6  
   creating: drop-in/.git/objects/f7/
 extracting: drop-in/.git/objects/f7/4ac398be94f10e2c71a05bcbe4f4103261f339  
 extracting: drop-in/.git/objects/f7/8a281620ddd2843ee1cde3877867d72ab25f19  
   creating: drop-in/.git/objects/d5/
 extracting: drop-in/.git/objects/d5/7c91383e3ca8a2decd39dd7c51568749f97420  
 extracting: drop-in/.git/objects/d5/3e0de35a215122729cfe040e3072f267db69c8  
 extracting: drop-in/.git/objects/d5/624bc9bf67986e22034fc942b5c3bf61c227a7  
   creating: drop-in/.git/objects/82/
 extracting: drop-in/.git/objects/82/25871ef1ec3a2d9e1c53f09cf891b9af686106  
 extracting: drop-in/.git/objects/82/a79cf5ba42497c3a4b25434770084173a854bf  
 extracting: drop-in/.git/objects/82/b485dcebee3c11b53cb509b5b608ee0c478950  
   creating: drop-in/.git/objects/ad/
 extracting: drop-in/.git/objects/ad/c6e1dbe8529d494c7e600a82e621efbb662098  
 extracting: drop-in/.git/objects/ad/64ac92e3d8268dc56a53077e68db167be9810b  
 extracting: drop-in/.git/objects/ad/76a8c2a634079ce16838c9e26cf82f17c5825d  
   creating: drop-in/.git/objects/78/
 extracting: drop-in/.git/objects/78/af437961a7670b6a3c515287374d85d88d1003  
 extracting: drop-in/.git/objects/78/39a19c544cac2e2a941d1a7ce39bcd09b1ac80  
 extracting: drop-in/.git/objects/78/8da73efb1a5c3777e977ac25bd6877b1560327  
   creating: drop-in/.git/objects/39/
 extracting: drop-in/.git/objects/39/a75a1857d6a467f10e9333d8640463f5b898f9  
 extracting: drop-in/.git/objects/39/8869e55ce5ee63cc49e4e7dfa9b866b6f02b50  
 extracting: drop-in/.git/objects/39/3d3e45fc9fadb8ec9e93fa29e04e7bb9dc4bb9  
 extracting: drop-in/.git/objects/39/8ec2744fbf04c903a0bb0aafeb521db4642a14  
 extracting: drop-in/.git/objects/39/48a257e035894ea2d63d633acca3d9b8dc369f  
 extracting: drop-in/.git/objects/39/62365a467471e74387a5e81d4d9755044c1443  
   creating: drop-in/.git/objects/2f/
 extracting: drop-in/.git/objects/2f/5214f85e22a4a1dfe240643ad003fe18cc8a90  
 extracting: drop-in/.git/objects/2f/737e975561c4c1d64962757b828c98b47bd1e4  
 extracting: drop-in/.git/objects/2f/5d1ac97f734adb800446b8a4fabfdbfa6ee0c2  
 extracting: drop-in/.git/objects/2f/235547d6cb810fa08481a7abf8e7eceafa1227  
 extracting: drop-in/.git/objects/2f/ba0884f44ccbab33a550114114542029077ff8  
   creating: drop-in/.git/objects/59/
 extracting: drop-in/.git/objects/59/6db5a4dbd3798247a39b14af6096be70815e8a  
 extracting: drop-in/.git/objects/59/86612234fa04740370f5f1e1754ce4a7f426cb  
   creating: drop-in/.git/objects/a4/
 extracting: drop-in/.git/objects/a4/8e2e5276ba468f1bb00d330fa9e796d7f16b6d  
 extracting: drop-in/.git/objects/a4/331e45dcdf400d29bccc1712bd8ba107501db9  
   creating: drop-in/.git/objects/7f/
 extracting: drop-in/.git/objects/7f/4c69856ef7949d9facbaaee6b31dd32921f23b  
 extracting: drop-in/.git/objects/7f/264491a38840436901ac1e86952aebe17372dc  
   creating: drop-in/.git/objects/96/
 extracting: drop-in/.git/objects/96/7bd5633e19150a73f24ba1ef32e2671b25ae4a  
   creating: drop-in/.git/objects/e6/
 extracting: drop-in/.git/objects/e6/24a50561ec236051d62005edd11d1466d5363b  
 extracting: drop-in/.git/objects/e6/694b72225db170d8e7a949681a20bce46235ed  
   creating: drop-in/.git/objects/be/
 extracting: drop-in/.git/objects/be/b6d5218aa27bb30f7aaa441c66aa5c90b2641f  
   creating: drop-in/.git/objects/f3/
 extracting: drop-in/.git/objects/f3/8f6c5ea806a2e6a6bffefca534e4d7db8176d2  
 extracting: drop-in/.git/objects/f3/1f4ef68afecfc69d25566a20fc2f017474f29d  
 extracting: drop-in/.git/objects/f3/d5fe38471c7cc6a40ade11a0fd27dd2c7bb43c  
   creating: drop-in/.git/objects/bc/
 extracting: drop-in/.git/objects/bc/1d934836580b8d35a68b866c4f23594327e4a2  
 extracting: drop-in/.git/objects/bc/c6fadb69a928a00bf54c55ddab8d886dcc5c63  
   creating: drop-in/.git/objects/c2/
 extracting: drop-in/.git/objects/c2/abe3728a16a872925294060469f44deabdff5b  
 extracting: drop-in/.git/objects/c2/5739bcee22aa7aac1fce720e40ab7b1d0ca52d  
 extracting: drop-in/.git/objects/c2/ec05505c021aaba9e574354909507d9425d3b0  
   creating: drop-in/.git/objects/15/
 extracting: drop-in/.git/objects/15/100dc31ed7b11499745d1c3eea2bc0bbe0f6ba  
   creating: drop-in/.git/objects/41/
 extracting: drop-in/.git/objects/41/ad33c306de44bab885d34c056b440b71209dbf  
 extracting: drop-in/.git/objects/41/6d9652b65b6e3baeb01e4a79cfefe8ddd117c9  
   creating: drop-in/.git/objects/a6/
 extracting: drop-in/.git/objects/a6/dbbb8616c8e80aea4c70437e472bb39b44327d  
 extracting: drop-in/.git/objects/a6/5d446e7a810e24b574f9b0b9ae5fe346113dbe  
 extracting: drop-in/.git/objects/a6/d778f3d13d1b41c4b2a30d8f37cefe42904f9d  
   creating: drop-in/.git/objects/4f/
 extracting: drop-in/.git/objects/4f/fe3f3891701c48219b36e6693b20db47bc4cee  
 extracting: drop-in/.git/objects/4f/333f7e274c9981beff7a9108dc184633624f2b  
   creating: drop-in/.git/objects/fe/
 extracting: drop-in/.git/objects/fe/34ec9313b168336b50cd176989db25db9aeb2f  
 extracting: drop-in/.git/objects/fe/40cc6f4f5a432d0db0019259d67ac7c623629c  
 extracting: drop-in/.git/objects/fe/c32161420f3ceb0bead7d3575cb848a7fc1e68  
   creating: drop-in/.git/objects/ca/
 extracting: drop-in/.git/objects/ca/bbfa895493d8b7efb690cdd155da9d01a2ffcf  
 extracting: drop-in/.git/objects/ca/b4b6883c26d0332efa35d9d8e34efdc1a74560  
 extracting: drop-in/.git/objects/ca/bc7239b02bf8003095d858e1cad6093038044f  
 extracting: drop-in/.git/objects/ca/bb8fa0e809aba138d441f1f3d7a89736e4a018  
   creating: drop-in/.git/objects/86/
 extracting: drop-in/.git/objects/86/80d9b49c83ff2ed66c7c61dd15f32c0943fd75  
   creating: drop-in/.git/objects/1b/
 extracting: drop-in/.git/objects/1b/b3143e31917268002979e9aa19c29cccd2e45d  
   creating: drop-in/.git/objects/40/
 extracting: drop-in/.git/objects/40/a9c345b7cda7cf5ddbb0c6ac8ae337dcecfac5  
 extracting: drop-in/.git/objects/40/c08eafaf5b834e56485c35d67db2ebaa58cdaa  
 extracting: drop-in/.git/objects/40/7578ddf788345c377ba94bb06faae2bd29c721  
   creating: drop-in/.git/objects/49/
 extracting: drop-in/.git/objects/49/0627654e94abc30bd84a49765c6e1a7df63233  
   creating: drop-in/.git/objects/c7/
 extracting: drop-in/.git/objects/c7/d625fac04a1ec6ba6756624b1aeadff4da2de1  
 extracting: drop-in/.git/objects/c7/1da57e22e4c3156d9a53c24052d9f163d51e27  
 extracting: drop-in/.git/objects/c7/45cd3269b90a8124f1cc5df0923ee0710c9e60  
   creating: drop-in/.git/objects/4e/
 extracting: drop-in/.git/objects/4e/029046c3762c7023a260637bbaed672a31cec4  
 extracting: drop-in/.git/objects/4e/3a7f7ed5364faea5ce2c008fc2c7439467400b  
 extracting: drop-in/.git/objects/4e/54af3493fe290421e65f79160ddb9652547a02  
 extracting: drop-in/.git/objects/4e/2ef83d21ccd3cd552f78df88e53cbd0c2c9757  
   creating: drop-in/.git/objects/83/
 extracting: drop-in/.git/objects/83/9ec4718248a1a012e6bf1ff9fb971258d40af2  
 extracting: drop-in/.git/objects/83/b351b39ec6783d64d12475b4286883c6fffa97  
 extracting: drop-in/.git/objects/83/5da06d82406a132376acbfd140d08d781854b9  
 extracting: drop-in/.git/objects/83/9258e662b390bdc71864f543ee35791d09b324  
   creating: drop-in/.git/objects/72/
 extracting: drop-in/.git/objects/72/7c24223aa1511557a07b9e3c604e85662adb94  
   creating: drop-in/.git/objects/f0/
 extracting: drop-in/.git/objects/f0/3996ae01ef0c14374f8d059ea96dbf8166d97a  
 extracting: drop-in/.git/objects/f0/3f631a70d9f81cde8d975bd731ed09f1aef17a  
 extracting: drop-in/.git/objects/f0/336d2f28773143f81e6390fdd2283f3bea3df8  
 extracting: drop-in/.git/objects/f0/e5f4947f16b85da9a9b6cdeaf2b217e9d1e7f6  
 extracting: drop-in/.git/objects/f0/6d36b2af02eed9e17be16d65814ac98d789903  
 extracting: drop-in/.git/objects/f0/1397a1f4dd7529a912444de927d5d53dfb39da  
   creating: drop-in/.git/objects/aa/
 extracting: drop-in/.git/objects/aa/87165d003c55f6e8bd9edd4472dacc7fb6fe94  
 extracting: drop-in/.git/objects/aa/3e29ccb1390708b49fb877630d6c0d5b427454  
 extracting: drop-in/.git/objects/aa/3eddd97065d9d911d48ccd33f7677b5abe9b85  
 extracting: drop-in/.git/objects/aa/d62b5c0ee68e5ac3ad7703add70c1c5b13c7a1  
 extracting: drop-in/.git/objects/aa/1115e1aa12214562dfd80848f487fe750f2154  
   creating: drop-in/.git/objects/b5/
 extracting: drop-in/.git/objects/b5/8db57c7079b053defcfc36a2540f57e09f782a  
 extracting: drop-in/.git/objects/b5/642aae1fea0d9004028e1b5ea69c82397124ef  
 extracting: drop-in/.git/objects/b5/4da76ea4cbf4409093eef344c101e05ff8502a  
 extracting: drop-in/.git/objects/b5/e93d4c9f7df6b5f4ccd6cf52e1de1bc758c580  
 extracting: drop-in/.git/objects/b5/89a17bb405024d8688c71ff58795fb9bb45bd6  
 extracting: drop-in/.git/objects/b5/96f15c7f237661d95b8fc0b2b0ce15db3ea41a  
   creating: drop-in/.git/objects/5f/
 extracting: drop-in/.git/objects/5f/03d6dee77faded49d2240516014bbfd6fbad11  
 extracting: drop-in/.git/objects/5f/e66c5e92669f96192642b8ed04a5224c13d20a  
   creating: drop-in/.git/objects/d0/
 extracting: drop-in/.git/objects/d0/412fed85531ef64cfaa46c2b60020b14230697  
 extracting: drop-in/.git/objects/d0/dd472f4630ce024e3e1a7c9f07062de055edd6  
 extracting: drop-in/.git/objects/d0/cdeceed96897b7a0a90afa2d9d63662274be40  
   creating: drop-in/.git/objects/50/
 extracting: drop-in/.git/objects/50/68d9835e67177806769d7f3ff49157e2a65c10  
 extracting: drop-in/.git/objects/50/fbd849ebd66a6d91af8025de6d15dac6d2ab8d  
 extracting: drop-in/.git/objects/50/effe474542656446f66b2af2067e82fe8c47b4  
 extracting: drop-in/.git/objects/50/ce0610ab05bf0be569971bb6fb3a994d647b09  
 extracting: drop-in/.git/objects/50/ea323a08ef4cf6d6631c2f2c115179c3cf7af9  
 extracting: drop-in/.git/objects/50/6c5e2c14cefb1cad8cc82b8f5174c3e3cc8189  
 extracting: drop-in/.git/objects/50/fd56ec5cff118d59803a1cb42d3bdafd5ccc41  
   creating: drop-in/.git/objects/7b/
 extracting: drop-in/.git/objects/7b/d32df406e989d2e261b5f59e92f11019825003  
 extracting: drop-in/.git/objects/7b/c417ccf2e994123e43ff4eef807d87e5c0836a  
 extracting: drop-in/.git/objects/7b/3229ba732ba06413f0f648ae92d238305f9259  
 extracting: drop-in/.git/objects/7b/a08552684f651af87716c33d283740cc5541f5  
 extracting: drop-in/.git/objects/7b/8cf7047def4e0d5bf73dcce9a521ff151d8a95  
   creating: drop-in/.git/objects/0d/
 extracting: drop-in/.git/objects/0d/8c4fb5006be67c1a4628ed83ed3e0d8c6b41cb  
 extracting: drop-in/.git/objects/0d/dc58521cb7f6a8593423f18427b904c58d5db5  
 extracting: drop-in/.git/objects/0d/172fc8db3d7ee1cc373dde3bd36d293d1934ca  
   creating: drop-in/.git/objects/1d/
 extracting: drop-in/.git/objects/1d/1b61ca94f6e6d90800545d129e6124985fb81e  
 extracting: drop-in/.git/objects/1d/cfe7c6fa28d160ec056b0eba8a47fcde34be1b  
 extracting: drop-in/.git/objects/1d/109145f31c8e5e7bd0dbd497dfceb104cd6549  
   creating: drop-in/.git/objects/13/
 extracting: drop-in/.git/objects/13/20a673faa5020ef41853b3b28c8076e34a0c32  
 extracting: drop-in/.git/objects/13/9ef09a130daf8e4e05511ee9e8c3f6421bb9d6  
 extracting: drop-in/.git/objects/13/8c177182fe7382022d02b3a81ee479c8e9b345  
 extracting: drop-in/.git/objects/13/cf9d3b4ffafb53343a15d6b49b369864074976  
   creating: drop-in/.git/objects/cb/
 extracting: drop-in/.git/objects/cb/51c12e13913dd7386f04a235b8275d8640ffae  
   creating: drop-in/.git/objects/a1/
 extracting: drop-in/.git/objects/a1/d0535280a6c61e37a709fd878a0f9eeff3775b  
 extracting: drop-in/.git/objects/a1/37d4107aee7884836620d59f1f95e3f750577b  
   creating: drop-in/.git/objects/c6/
 extracting: drop-in/.git/objects/c6/24a2f6ecc1e5c0611a798562f05f425409a73a  
 extracting: drop-in/.git/objects/c6/45d278082242da2ed43927a8d4982a827137ea  
 extracting: drop-in/.git/objects/c6/499bce52cec44f5e94def9e5854412fe97152d  
 extracting: drop-in/.git/objects/c6/0fcfbb6788fe912124e7f3eaff45d72a9d8fcb  
 extracting: drop-in/.git/objects/c6/bfb4720990eeb2cfcb6abce91f69b2671a71fe  
   creating: drop-in/.git/objects/fb/
 extracting: drop-in/.git/objects/fb/1ce31a84856a1ca77b65712131285e831a309d  
 extracting: drop-in/.git/objects/fb/d7083e6de2d75a4b797a9f6a9875b885885b15  
 extracting: drop-in/.git/objects/fb/83546974d714c6667dee0255ef7a503d7fcab0  
   creating: drop-in/.git/objects/99/
 extracting: drop-in/.git/objects/99/860e89d69c33f0355315eef770da82a91cbb0a  
 extracting: drop-in/.git/objects/99/a2357215ebcd2bf2429b0d4ad9ef77a8536c2f  
 extracting: drop-in/.git/objects/99/5449c719312a10db56c249bd23755cef533cc4  
 extracting: drop-in/.git/objects/99/6d55a9cdf693104af90e387d27c1d6e456e918  
 extracting: drop-in/.git/objects/99/f12109ac9765e05959f9136d63413b248ae7b6  
 extracting: drop-in/.git/objects/99/44463a578521c39715bbd8b85cb33d5f18045e  
   creating: drop-in/.git/objects/87/
 extracting: drop-in/.git/objects/87/5209919c322121a0ffd5b97361a4c695d72b3f  
 extracting: drop-in/.git/objects/87/cec0500c60ce791995152365ed46b651775c43  
 extracting: drop-in/.git/objects/87/36ef94561f1bb05ba06cadb76aaf0e40a9430c  
 extracting: drop-in/.git/objects/87/93c4001f253a1735adca2b17c011b5e82f69b1  
 extracting: drop-in/.git/objects/87/7703e7c4038a1a8f0f7e312309fe0128f8660a  
   creating: drop-in/.git/objects/2d/
 extracting: drop-in/.git/objects/2d/366920936dd118d13e7f2baadc8584221581ba  
 extracting: drop-in/.git/objects/2d/35ac2671a7980696db462f25e4b0801ce87085  
   creating: drop-in/.git/objects/c0/
 extracting: drop-in/.git/objects/c0/cca43ebae9f43c419341505749d24dd0556418  
 extracting: drop-in/.git/objects/c0/243a4d84896a00c999a2da95c423f75cf988a1  
 extracting: drop-in/.git/objects/c0/74b3990846b89306a76e243090a8ab70dc0fca  
   creating: drop-in/.git/objects/8f/
 extracting: drop-in/.git/objects/8f/726bfa87c4b7c5ba6b12e472ab39887bc7424c  
 extracting: drop-in/.git/objects/8f/50804fd23a8ee533479a31189b33ae988132db  
 extracting: drop-in/.git/objects/8f/0eb9ee3dd2bb89424070d72f137dd1ba871e32  
 extracting: drop-in/.git/objects/8f/6c52985ab99293fad6c37b2e4cd0af82b0ff9a  
 extracting: drop-in/.git/objects/8f/921b7d17004291786aec4dab12410641d97e64  
   creating: drop-in/.git/objects/f9/
 extracting: drop-in/.git/objects/f9/b1694c1421de97f4605a2c8bd06f16068e96e0  
 extracting: drop-in/.git/objects/f9/1f4b32fee0f856043861acde543ced00d45265  
 extracting: drop-in/.git/objects/f9/e2acc3242767372e6d9e7b057c72969be0a73e  
   creating: drop-in/.git/objects/84/
 extracting: drop-in/.git/objects/84/d7f84e8f5cbb98a29bae6c952b69241714fe32  
 extracting: drop-in/.git/objects/84/3284b29b6c437b179b48fefc97afca55249b58  
 extracting: drop-in/.git/objects/84/ff7bc8e6e79dc11ceae99f4e9bcca18a15b178  
 extracting: drop-in/.git/objects/84/af6859e40d81ed0cd9a8de820fdf66532f6b30  
   creating: drop-in/.git/objects/73/
 extracting: drop-in/.git/objects/73/9c31edb989d6eca0fa400ef39300ca5760602e  
   creating: drop-in/.git/objects/6a/
 extracting: drop-in/.git/objects/6a/084d4135041ff94e0b8c2984a86a53ca1be1e0  
   creating: drop-in/.git/objects/38/
 extracting: drop-in/.git/objects/38/c7c1ad3ce7eafe10edd6542d19880e8491dcbf  
 extracting: drop-in/.git/objects/38/4ec7d9f3666449ff3d67b27c3477a2b40a7e8f  
 extracting: drop-in/.git/objects/38/0e9bbecb13d8d6bd8175684089126bac60a8d9  
 extracting: drop-in/.git/objects/38/79dbcd543abe6e43c1c9cac5bed8b5796af9bc  
   creating: drop-in/.git/objects/e0/
 extracting: drop-in/.git/objects/e0/d53ecb450656fd410a9b2cf25313e3c8b45f8f  
 extracting: drop-in/.git/objects/e0/871a7e7f3bf1b77d24021d794405b19f7b4e02  
   creating: drop-in/.git/objects/b1/
 extracting: drop-in/.git/objects/b1/cf44ccb19c4c9fda3bb27315c8065801123d47  
   creating: drop-in/.git/objects/70/
 extracting: drop-in/.git/objects/70/64763a486e2cfc9adfd8eb1eada0d767416642  
   creating: drop-in/.git/objects/76/
 extracting: drop-in/.git/objects/76/72b9fdbb6495b86a26817ccfec6d3614ebbcb5  
 extracting: drop-in/.git/objects/76/5cd459a6a9f0fe537f148075f49ababfd5fda7  
   creating: drop-in/.git/objects/1e/
 extracting: drop-in/.git/objects/1e/8cee6a50ce976f42e279a87b5639c4420c3080  
 extracting: drop-in/.git/objects/1e/1764b960055a2b4a07bfdcce7a488925975c1a  
 extracting: drop-in/.git/objects/1e/2669c4ba139f84e23fe260c6d4d1ababa0c6c1  
 extracting: drop-in/.git/objects/1e/88af8f44b72b922dfb5ed0823840480de49241  
   creating: drop-in/.git/objects/75/
 extracting: drop-in/.git/objects/75/c11abe7cb6130711d2160e2e79b826cd62ac56  
 extracting: drop-in/.git/objects/75/8e8ead8268a3a6dc5861e0c2a51980dbc4c05c  
 extracting: drop-in/.git/objects/75/8ecc145d50744df1d20c68fcc6c91d98e06401  
   creating: drop-in/.git/objects/97/
 extracting: drop-in/.git/objects/97/dedcd094a7f94025edca1e7c1c96a0da04858c  
 extracting: drop-in/.git/objects/97/c693380aac31e19e202081af86c6c195280cc4  
 extracting: drop-in/.git/objects/97/92ca9570e90c56d08ea145e6cef17dfcf261d9  
   creating: drop-in/.git/objects/62/
 extracting: drop-in/.git/objects/62/c9a1b832cc3335fe5c00fa62544a92628768b7  
 extracting: drop-in/.git/objects/62/8ddd97bd890557552cdf9770e0f47a7b8e2f59  
   creating: drop-in/.git/objects/27/
 extracting: drop-in/.git/objects/27/98aba5dd7615c95dde3975efef800cd0444fa5  
 extracting: drop-in/.git/objects/27/1dc78602e113aba1b29ab7d05a56b5c5fcea4d  
   creating: drop-in/.git/objects/17/
 extracting: drop-in/.git/objects/17/943abcb3ecba4d7d3e9f86a06ecfde79f2d50e  
   creating: drop-in/.git/objects/fa/
 extracting: drop-in/.git/objects/fa/85ae330b1dfa27d7eda422a65ab36ddba00c27  
 extracting: drop-in/.git/objects/fa/c60235a8bb6d6cb96def1d48086ccc5b5e5dd0  
   creating: drop-in/.git/objects/8c/
 extracting: drop-in/.git/objects/8c/628848a83aab37c61f7a5cc0531985fa71bfe6  
 extracting: drop-in/.git/objects/8c/1f8a30b17a3849beda736acbfa2d6d0eb96a8b  
 extracting: drop-in/.git/objects/8c/4025e6178cdb0795a3c177c61752372afec838  
 extracting: drop-in/.git/objects/8c/bda7b53868f706a8787ec92f8a0ab59e67bd6c  
   creating: drop-in/.git/objects/30/
 extracting: drop-in/.git/objects/30/c90a00299b8c513b589738cf954822204e74c2  
 extracting: drop-in/.git/objects/30/44675356fa6df2c18689ddd21c8bdc4ccfdfe8  
   creating: drop-in/.git/objects/34/
 extracting: drop-in/.git/objects/34/fc62154ef9064923a39c0d73d73c90a9eac572  
 extracting: drop-in/.git/objects/34/2db70d67c5ea35e41dbb09335c5d33d13bf5d0  
   creating: drop-in/.git/objects/67/
 extracting: drop-in/.git/objects/67/5d09502b580f594f31c8cc3c61099a70904a79  
 extracting: drop-in/.git/objects/67/9ef720ce0287694deea2dcd8cfb26e11969043  
 extracting: drop-in/.git/objects/67/522fa2c79185fda97986c510c87dc50cecd8be  
   creating: drop-in/.git/objects/e9/
 extracting: drop-in/.git/objects/e9/591ca0e3f3796989daf5b7cf88359bde6be7ab  
 extracting: drop-in/.git/objects/e9/0c347ab8dc8b2aaee095409d441d1edbf94c3b  
   creating: drop-in/.git/objects/bf/
 extracting: drop-in/.git/objects/bf/85fcf9d2ac887c4ee69703531a83108284a798  
   creating: drop-in/.git/objects/cf/
 extracting: drop-in/.git/objects/cf/f3a0fbedd1df80db99ed4ab130d0c947e262fa  
 extracting: drop-in/.git/objects/cf/c3a35eb1075f662bec3660d67fb51c0a952e6b  
   creating: drop-in/.git/objects/95/
 extracting: drop-in/.git/objects/95/e929dff8b95f788d3e6d3317264cd3912ea68c  
 extracting: drop-in/.git/objects/95/ba846ab9d0ae361f352c59eb7dced261a15f6a  
 extracting: drop-in/.git/objects/95/dbf853dcf9c24c645ca82e935215a7c2abaf38  
 extracting: drop-in/.git/objects/95/e629e8914c5504ecaa83e9a69931ee891d5a66  
   creating: drop-in/.git/objects/94/
 extracting: drop-in/.git/objects/94/7fd441fec8f1b9a0347d13a5fc6c380b337fb9  
 extracting: drop-in/.git/objects/94/d85e21ecf0b603fb8704f4353a05dd8835273e  
 extracting: drop-in/.git/objects/94/cdf8f3030c8cc09258a5cd67ff433d52091efe  
   creating: drop-in/.git/objects/04/
 extracting: drop-in/.git/objects/04/47da911c8da79cdc01d6efbf52aa1fe1190947  
 extracting: drop-in/.git/objects/04/f001c4c53156138b49b9d1259f0f7c2ad54582  
 extracting: drop-in/.git/objects/04/c58d93af256f297465cf59c36771783c1b9760  
 extracting: drop-in/.git/objects/04/c4316590f7bd6056e926d49a53107115fa2960  
   creating: drop-in/.git/objects/21/
 extracting: drop-in/.git/objects/21/35f6a8156af8df71d0fa2e9f088eec5c434267  
 extracting: drop-in/.git/objects/21/19647f1392c6c29e77cda7edeb1096f678c028  
   creating: drop-in/.git/objects/55/
 extracting: drop-in/.git/objects/55/558298076e0bda81ee341173f1639193f54af3  
 extracting: drop-in/.git/objects/55/9d62f29ad7b5d5f8cc5988039a10a36fe19744  
   creating: drop-in/.git/objects/fc/
 extracting: drop-in/.git/objects/fc/c9ebb16653ddf45aacc7552fda064d3224fa17  
   creating: drop-in/.git/objects/8e/
 extracting: drop-in/.git/objects/8e/49cb59e747563c3887a74471c1c3a06cacb292  
 extracting: drop-in/.git/objects/8e/b6174289a9a0579de3f4cf496c07d650a902e4  
 extracting: drop-in/.git/objects/8e/4b54cd7caebad305f981db9d430cdf756fb099  
 extracting: drop-in/.git/objects/8e/e117742fba13db33287a80222ab2e30ccc04b9  
   creating: drop-in/.git/objects/7c/
 extracting: drop-in/.git/objects/7c/276b89099ba9ac9b312d8a1a263802d24248c3  
   creating: drop-in/.git/objects/bd/
 extracting: drop-in/.git/objects/bd/0fd69fd2c1f8ba411c9d05faa4ace9f0670bf0  
 extracting: drop-in/.git/objects/bd/7c2f9c5d330be001284b360ef4702bc7883f9b  
   creating: drop-in/.git/objects/a9/
 extracting: drop-in/.git/objects/a9/4a76a4f4fa917d54fc3a4cbb5d155333a297e6  
 extracting: drop-in/.git/objects/a9/0e826a219dd1a5bc359af399018ac33d12b329  
   creating: drop-in/.git/objects/f4/
 extracting: drop-in/.git/objects/f4/550b69ab3cf1a11e0dd5ee6f80ef8bda45f0d7  
 extracting: drop-in/.git/objects/f4/23c63ea34ef04928ebdbc1a55dbaf4d972bb06  
 extracting: drop-in/.git/objects/f4/37c91d67acc90f5de775b4d9ce651001260c4d  
 extracting: drop-in/.git/objects/f4/a918f9716eb35236190dbebe5b693f6dc64c58  
   creating: drop-in/.git/objects/2a/
 extracting: drop-in/.git/objects/2a/ef13c7a7f7246040f8ecc5107c37650c85fde3  
 extracting: drop-in/.git/objects/2a/4458a8a8d319d3f7123161fdfb91c391db5839  
 extracting: drop-in/.git/objects/2a/69dbf722334dc0736fc5bc8cee9bd6c684de31  
 extracting: drop-in/.git/objects/2a/7f79febee6001af4dd73bf3b56e40d78cb68ea  
 extracting: drop-in/.git/objects/2a/32be5799699872a8e3830586f18afcd8ea4db3  
   creating: drop-in/.git/objects/f2/
 extracting: drop-in/.git/objects/f2/d0d06d21c89e0652ff21d2e7819a980f19c692  
 extracting: drop-in/.git/objects/f2/f5691b08e2902d274d64a6bec0328497324154  
 extracting: drop-in/.git/objects/f2/70f5689b68ad7eb5df15388557acd6366203fa  
   creating: drop-in/.git/objects/de/
 extracting: drop-in/.git/objects/de/d372de451b092a0e7ce301f86203142a737bd2  
   creating: drop-in/.git/objects/91/
 extracting: drop-in/.git/objects/91/9cfda0342c217a5676e422894e77c30dd88a78  
   creating: drop-in/.git/objects/35/
 extracting: drop-in/.git/objects/35/07f1d86f80cbac03505e13e5c769e3754e164e  
 extracting: drop-in/.git/objects/35/3c810c580c89fb2f22a2518b311b135c961095  
 extracting: drop-in/.git/objects/35/623d28f7e8ec8864d00b84da8b93a88177f9c5  
   creating: drop-in/.git/objects/9c/
 extracting: drop-in/.git/objects/9c/81a491afe91b347e6158fca79d3470918804a5  
   creating: drop-in/.git/objects/b0/
 extracting: drop-in/.git/objects/b0/b586e15ee203ed7822a867a803092dd0cb269c  
 extracting: drop-in/.git/objects/b0/22c372409541b1d2e615cd26cf3a6b59a35508  
   creating: drop-in/.git/objects/cd/
 extracting: drop-in/.git/objects/cd/14c619d1d66fd62acbbb991ef0e9843c5256e2  
 extracting: drop-in/.git/objects/cd/3466a2cf7ca251ac0443c6ac69774799b5c54b  
   creating: drop-in/.git/objects/10/
 extracting: drop-in/.git/objects/10/402ce908a0e5430f4a0a6223d50ef7d3943b12  
 extracting: drop-in/.git/objects/10/6abfaf1e50495a02807ae7a9af1aba181e95bd  
 extracting: drop-in/.git/objects/10/9ae7b95d373b928b72c56d52316842dd378e9a  
   creating: drop-in/.git/objects/d7/
 extracting: drop-in/.git/objects/d7/144691be2426d02e3858b318454c78021aa1fd  
   creating: drop-in/.git/objects/66/
 extracting: drop-in/.git/objects/66/bdf7d6cfe2c0b50b44155698e1ddf46d0ad811  
 extracting: drop-in/.git/objects/66/bf73999b9a186ec3fc0191ea6b41c8a99d0a2d  
   creating: drop-in/.git/objects/33/
 extracting: drop-in/.git/objects/33/a0a6eff720a6519c2a22068c4ab7826cf5b120  
   creating: drop-in/.git/objects/e2/
 extracting: drop-in/.git/objects/e2/b3b831c30a0ddaf27aaffba6a23b55cdaa60eb  
 extracting: drop-in/.git/objects/e2/c47a7a9c2b46cf189fef2d848122fee3641e34  
 extracting: drop-in/.git/objects/e2/71500fc77eac9d2d4b00e4a80d0a9f6b676b61  
   creating: drop-in/.git/objects/ef/
 extracting: drop-in/.git/objects/ef/fb57f3237249654f0bfbb88efa5357327672b2  
   creating: drop-in/.git/objects/a0/
 extracting: drop-in/.git/objects/a0/78de17ef3d3d62cbb85c419959d15a693c58fc  
 extracting: drop-in/.git/objects/a0/5b9b506d6fee5b1cba1ae65fd90acea10c8ac2  
   creating: drop-in/.git/objects/5e/
 extracting: drop-in/.git/objects/5e/6221a95b9e9017d8bb31b58a70090c111529f9  
 extracting: drop-in/.git/objects/5e/53ebbbe7c93e647fd54779e2d5bba58bcdf47f  
 extracting: drop-in/.git/objects/5e/91fb2644b9977be6e68b55498fc8f0a1d33639  
   creating: drop-in/.git/objects/16/
 extracting: drop-in/.git/objects/16/dee57339469c1431c17329205e00203d7d3648  
 extracting: drop-in/.git/objects/16/87f95c6e8ca5c10e377f479500c266eb43e203  
   creating: drop-in/.git/objects/64/
 extracting: drop-in/.git/objects/64/a3457379b293d414cbf1fd6202a9c034ca0a0a  
   creating: drop-in/.git/objects/4a/
 extracting: drop-in/.git/objects/4a/9e57416c3cd3863e54ec0f345f08280778c750  
   creating: drop-in/.git/objects/42/
 extracting: drop-in/.git/objects/42/8f980d0a6a47dac2e74522ccb0890c96b0a579  
 extracting: drop-in/.git/objects/42/991a2403dccdf0863a65d50e7d29bd339d22c1  
 extracting: drop-in/.git/objects/42/b8ffef76eb4f8418d5560146e33cc579be363d  
 extracting: drop-in/.git/objects/42/f79e7b0c7614bee6885a2201219f4902b9f13c  
   creating: drop-in/.git/objects/a8/
 extracting: drop-in/.git/objects/a8/c045fb5c6847814c157afb105112394b5dff1d  
   creating: drop-in/.git/objects/77/
 extracting: drop-in/.git/objects/77/5c9b801f48f5105e2016bad196d1108bffd99d  
 extracting: drop-in/.git/objects/77/134a232e6ecdec2beb9627c5a764d3dd1cf943  
 extracting: drop-in/.git/objects/77/5dd52479d8faaf061368c56436031445a247a4  
 extracting: drop-in/.git/objects/77/64729ab2358988a0350e7926dd00d039cbc68f  
 extracting: drop-in/.git/objects/77/c4f36885e4efeff1c81cdea4c4b11babe73053  
   creating: drop-in/.git/objects/12/
 extracting: drop-in/.git/objects/12/04594aa343f9bd0e8dc2b687d07696f7b49d21  
 extracting: drop-in/.git/objects/12/da8e742c14a99a3c9bc94e07f8ebca8b4ef591  
   creating: drop-in/.git/objects/a7/
 extracting: drop-in/.git/objects/a7/f7983b6fde20a861f0b2289bcb8aafd178abe9  
   creating: drop-in/.git/objects/9f/
 extracting: drop-in/.git/objects/9f/20582214cebda754c4376bd1ded9bbc9051802  
 extracting: drop-in/.git/objects/9f/32cd1d5537bc51b9bb122d0631f0f7ea10f56b  
   creating: drop-in/.git/objects/06/
 extracting: drop-in/.git/objects/06/d62ff31807a7d51d00a6cddcdcd0908b334c5e  
   creating: drop-in/.git/objects/05/
 extracting: drop-in/.git/objects/05/d92c9a3dddbd3c57a75fc3675834adac2021e1  
 extracting: drop-in/.git/objects/05/009e34da94563ee25fd868446a3af4b708cc0c  
   creating: drop-in/.git/objects/3a/
 extracting: drop-in/.git/objects/3a/2eb6f0a51cc59d47bb583ec10bcbbc35cc3812  
 extracting: drop-in/.git/objects/3a/0ef6f4edbd39f94539885e63f7f7098494ee93  
   creating: drop-in/.git/objects/9e/
 extracting: drop-in/.git/objects/9e/2debcbe8d2648fbe2859e584e59e1d165bceae  
   creating: drop-in/.git/objects/e8/
 extracting: drop-in/.git/objects/e8/5345fc5e50ab8d10718d93433bcd27e8b437e7  
 extracting: drop-in/.git/objects/e8/c15d80972914b5bfbb035e944af4a13a917bf9  
   creating: drop-in/.git/objects/c9/
 extracting: drop-in/.git/objects/c9/6bec94bf22ed02bb1e2af27792b16d1230b317  
 extracting: drop-in/.git/objects/c9/673945fb6c26b7cfc8bee099e239653f2dca9f  
 extracting: drop-in/.git/objects/c9/404b39ec1cd3628bcbb4e2fe5b5fdd7754ab8b  
 extracting: drop-in/.git/objects/c9/a271774149f2d899e2541ff910f92ff80fe099  
   creating: drop-in/.git/objects/7a/
 extracting: drop-in/.git/objects/7a/35052351d6eda972f60a042ea7e27b00c1d8dc  
 extracting: drop-in/.git/objects/7a/28ce3f6649f381149f8ab158fd11ee61a85603  
   creating: drop-in/.git/objects/cc/
 extracting: drop-in/.git/objects/cc/761d88a8cfe3c693a7622fc68ba67c78bb0f11  
   creating: drop-in/.git/objects/19/
 extracting: drop-in/.git/objects/19/72ac498fcbc38a67b858d0e0a2b3fc8c8fd798  
 extracting: drop-in/.git/objects/19/84798d3e2595fca2d01daa1ea17b848b129dd4  
   creating: drop-in/.git/objects/43/
 extracting: drop-in/.git/objects/43/aafd789ac914c70fa57e748f984afb635b8e5d  
 extracting: drop-in/.git/objects/43/6915c859f2f7dfdac9821e2c8474bdedabb178  
 extracting: drop-in/.git/objects/43/efe4b104f3196836fa03d3d22ccf5f192cb16b  
   creating: drop-in/.git/objects/bb/
 extracting: drop-in/.git/objects/bb/879bc610094e4d4f25cf4315ed1a4975f2e942  
 extracting: drop-in/.git/objects/bb/bc745921d7bf573d053e45c57b8baacc5e4fa7  
 extracting: drop-in/.git/objects/bb/53ad49c2f00aacae75a8c960b52177aeeddfba  
   creating: drop-in/.git/objects/90/
 extracting: drop-in/.git/objects/90/7049abfa43c8142586a2da7d5a7896d726ed11  
   creating: drop-in/.git/objects/60/
 extracting: drop-in/.git/objects/60/596d4774ceb368feb92851ce0deefac41b3504  
 extracting: drop-in/.git/objects/60/cced32d729e6fdef9cd94c8c8e46cc9dd10034  
   creating: drop-in/.git/objects/58/
 extracting: drop-in/.git/objects/58/a99f650f5c47a67a9fa779d2ab2c8863e7271a  
   creating: drop-in/.git/objects/f8/
 extracting: drop-in/.git/objects/f8/2c7227da88c28af1f5f05450e31c17755e3569  
 extracting: drop-in/.git/objects/f8/657d4c52339599dcaa701a4834fb2954db7f95  
 extracting: drop-in/.git/objects/f8/e8c5a1f0d3cf8eb50f598dde333cf3ceb17bcb  
 extracting: drop-in/.git/objects/f8/be1553fef22d92114b74833bed63da32c1d82a  
 extracting: drop-in/.git/objects/f8/9bbe15744eee2f55f7692e67e5f68687b66d61  
   creating: drop-in/.git/objects/69/
 extracting: drop-in/.git/objects/69/a7f6c861c75425fbc303a5733259b8dc227579  
   creating: drop-in/.git/objects/81/
 extracting: drop-in/.git/objects/81/754441b4beafbd4bede50db5573efab480f795  
 extracting: drop-in/.git/objects/81/59a7730b640e2ff70fdea54d8fa1d084329c13  
   creating: drop-in/.git/objects/4b/
 extracting: drop-in/.git/objects/4b/2131f479de49bd10df7d6edbfa7f473251b929  
   creating: drop-in/.git/objects/68/
 extracting: drop-in/.git/objects/68/f18734cf82717f956c685b0a009ef4587c5135  
 extracting: drop-in/.git/objects/68/7d39040e7412189da17d891b7e0a948a79d023  
 extracting: drop-in/.git/objects/68/3d28b689dba758b23155a541cb579bc47b3405  
 extracting: drop-in/.git/objects/68/add82005794e91d723d831042b329f64a7d5b6  
 extracting: drop-in/.git/objects/68/59e8a213c7c78aa49e8b6a694c400aff9132e7  
   creating: drop-in/.git/objects/9d/
 extracting: drop-in/.git/objects/9d/7b680aedfe6de60e42dd7996784fe6c9e9cb11  
   creating: drop-in/.git/objects/a3/
 extracting: drop-in/.git/objects/a3/3e53d8f15e1488660e171502926856a8a45da2  
 extracting: drop-in/.git/objects/a3/3d040cf3b535cf71090cecb51adabba7e5d62a  
 extracting: drop-in/.git/objects/a3/eca82422afa089692960b231fb4042dee91ec8  
   creating: drop-in/.git/objects/a2/
 extracting: drop-in/.git/objects/a2/0e0d4cd2725327a93b3c3f6f87a3eb9c6af128  
   creating: drop-in/.git/objects/eb/
 extracting: drop-in/.git/objects/eb/6f8a96a65c30265304c6cf90a2c2cc70b12f9f  
 extracting: drop-in/.git/objects/eb/af15247d986492cde3729d93c881c4b31ee41f  
   creating: drop-in/.git/objects/6e/
 extracting: drop-in/.git/objects/6e/0df3f726ceee9d34dafa1320245b804daf456a  
 extracting: drop-in/.git/objects/6e/16490b8cd01b1db097b0fc6bca96b34579fa9d  
 extracting: drop-in/.git/objects/6e/df6181cd11b531a95172a9e7c1e682c915dff4  
   creating: drop-in/.git/objects/ba/
 extracting: drop-in/.git/objects/ba/c43ba10970b5f5d410e4364a45f568f636d2e6  
   creating: drop-in/.git/objects/c8/
 extracting: drop-in/.git/objects/c8/9e0aea5328164a78724d9adb5a083361cc7d50  
   creating: drop-in/.git/objects/7e/
 extracting: drop-in/.git/objects/7e/a8acd65c36e77b5f01520e62608df45266ea98  
   creating: drop-in/.git/objects/46/
 extracting: drop-in/.git/objects/46/24576b1285404f09249f514539b9a2ac551af1  
   creating: drop-in/.git/objects/89/
 extracting: drop-in/.git/objects/89/f9826a480ca6ca6d7799696ca501801ebd5a2d  
 extracting: drop-in/.git/objects/89/b0546c1ea7ae7fdb7f476020254970783da4c0  
   creating: drop-in/.git/objects/ce/
 extracting: drop-in/.git/objects/ce/b95301016f3f560ea422b73514d3aa40435f75  
 extracting: drop-in/.git/objects/ce/9821af5faf41601d5db4b2be672dc08a4b6a13  
   creating: drop-in/.git/objects/e4/
 extracting: drop-in/.git/objects/e4/ab12d570403dc38df26b640b864b096a51f047  
 extracting: drop-in/.git/objects/e4/173dd1ed7989b9ed217b55563103fc7a455ada  
   creating: drop-in/.git/objects/26/
 extracting: drop-in/.git/objects/26/865fd4a713a01570bbe26e507ac2b3d57f12a9  
   creating: drop-in/.git/objects/00/
 extracting: drop-in/.git/objects/00/c70e48bec4b1c8f08de616108b06973e4482b6  
   creating: drop-in/.git/objects/ee/
 extracting: drop-in/.git/objects/ee/60797cb73c816c3a81dcf5050d92d63e30da05  
   creating: drop-in/.git/objects/5c/
 extracting: drop-in/.git/objects/5c/2efd6aac50b42464df2b09c66c6bec0e34158e  
   creating: drop-in/.git/objects/09/
 extracting: drop-in/.git/objects/09/7e8d8d421b79b65a6300b191de43daeae5a673  
 extracting: drop-in/.git/objects/09/0d4c1f8707086f7a0dfa2cef32a7715de87b64  
   creating: drop-in/.git/objects/3f/
 extracting: drop-in/.git/objects/3f/c0a3935bef24e475749d894d352546f0215b56  
 extracting: drop-in/.git/objects/3f/d245e163e476db5272562cdb971c6ca9c452da  
 extracting: drop-in/.git/objects/3f/9a39b6c8eb751399856c0cdf4fb78eac901120  
   creating: drop-in/.git/objects/dd/
 extracting: drop-in/.git/objects/dd/21ba351cd3a3c2bd5d1dafdde94504b8a8fcf3  
   creating: drop-in/.git/objects/56/
 extracting: drop-in/.git/objects/56/75cc5db27c1992bd7fefc0fc97d6cb230efb11  
 extracting: drop-in/.git/objects/56/11f02bbfed52af8c78eb92ec58a323bebf96da  
   creating: drop-in/.git/objects/df/
 extracting: drop-in/.git/objects/df/ec729b33d22f042cbdd1f17ba0cd94ae42281a  
 extracting: drop-in/.git/objects/df/aa56f00bda5b7bb5ac9e9f956bff5166f908b2  
   creating: drop-in/.git/objects/2b/
 extracting: drop-in/.git/objects/2b/ec963ed59fa9f1894b09651ca75d2a182ec846  
   creating: drop-in/.git/objects/79/
 extracting: drop-in/.git/objects/79/88b05d16fa0cb15de3f85fd00bb35143c4c70c  
 extracting: drop-in/.git/objects/79/4a68edae70a4c0d679bcd78d72139347e3fc1e  
   creating: drop-in/.git/objects/c3/
 extracting: drop-in/.git/objects/c3/a9230d0461471aab0b6ac8cc1c8212af903813  
 extracting: drop-in/.git/objects/c3/f1e4c4ca5540f8b9c41d3645a456fd2c4b0be4  
 extracting: drop-in/.git/objects/c3/d5617dd34def43d9ea808a54fa3fae7ae10595  
 extracting: drop-in/.git/objects/c3/322454b6edc19d358e6b203c55d18e8b3f8fcb  
   creating: drop-in/.git/objects/85/
 extracting: drop-in/.git/objects/85/af3bfc212f93c9ac6966f2970490b3829ba084  
 extracting: drop-in/.git/objects/85/68387709054bd6b2502904ccc79febec979465  
   creating: drop-in/.git/objects/07/
 extracting: drop-in/.git/objects/07/7372793088bb64ff1c77c511ade4aaf935fb7c  
   creating: drop-in/.git/objects/ec/
 extracting: drop-in/.git/objects/ec/34b502a3e5d65aa9cae28d06db86e63585199c  
 extracting: drop-in/.git/objects/ec/40791a1e909055767593897d221bd2353a8629  
 extracting: drop-in/.git/objects/ec/e28e68ca51fb18231ed28b7a3af3189f29d97b  
   creating: drop-in/.git/objects/9a/
 extracting: drop-in/.git/objects/9a/de87d5ce3ca8cd8396aa6d08130901e6dcf3d3  
   creating: drop-in/.git/objects/6d/
 extracting: drop-in/.git/objects/6d/bc74bbdc79d3ba6dea37c8a30d87b1f3550d3e  
   creating: drop-in/.git/objects/63/
 extracting: drop-in/.git/objects/63/d27302e2246a55a7d58421abd03c66832ddba3  
   creating: drop-in/.git/objects/88/
 extracting: drop-in/.git/objects/88/98b1406a69cd26cbef78f553896af14ab38510  
 extracting: drop-in/.git/objects/88/8b62a6a03787716848489e1ad4cac05406f150  
   creating: drop-in/.git/objects/db/
 extracting: drop-in/.git/objects/db/09ad7d37f9fcc6e7dc0f18ce398b3c698d2c3c  
   creating: drop-in/.git/objects/5a/
 extracting: drop-in/.git/objects/5a/5dfae8fecee517c79344717fa84f2837f96773  
 extracting: drop-in/.git/objects/5a/3742af4db3d8fd3694543ce7d3cf585f3a54d2  
   creating: drop-in/.git/objects/36/
 extracting: drop-in/.git/objects/36/dfb65b4b5a33fbb021e97d44b868a766baeb26  
   creating: drop-in/.git/objects/d1/
 extracting: drop-in/.git/objects/d1/913a31732230530317ac21800e4050c72f3306  
   creating: drop-in/.git/objects/54/
 extracting: drop-in/.git/objects/54/2ba0098dc8c6db6bccf90dbfcb97481cb303b5  
 extracting: drop-in/.git/objects/54/77d0787de388d72cb081275723d1c2870e13ac  
 extracting: drop-in/.git/objects/54/643fe396ef10dd3d5281477e6e66b135f5f9bc  
   creating: drop-in/.git/objects/da/
 extracting: drop-in/.git/objects/da/1a53e48533b2b678c7fc6d296e8eb91e0ca142  
   creating: drop-in/.git/objects/ae/
 extracting: drop-in/.git/objects/ae/1c80324e63713476a68abba480dca3be7a2d27  
   creating: drop-in/.git/objects/9b/
 extracting: drop-in/.git/objects/9b/7846d58b836230f04c17bf0b6916b5750cc655  
   creating: drop-in/.git/objects/08/
 extracting: drop-in/.git/objects/08/21bd8ca70239b9ec8e3ecf4a1f32b33ba84126  
   creating: drop-in/.git/objects/d8/
 extracting: drop-in/.git/objects/d8/680cb385d1bf08776bf1f657830088899a4f8c  
   creating: drop-in/.git/objects/8a/
 extracting: drop-in/.git/objects/8a/489645738a3df462a095c8761fd9fa80b2e578  
   creating: drop-in/.git/objects/dc/
 extracting: drop-in/.git/objects/dc/7d4433968be4318dd6a4b87d73b0bbfc7940db  
 extracting: drop-in/.git/objects/dc/247c99314dfb455049612aa999425630b776db  
 extracting: drop-in/.git/objects/dc/6c742fda3450425f824d927298d800b5a43d8b  
 extracting: drop-in/.git/objects/dc/bfd0e85c4454882cfab10a80ec591e54503bd8  
 extracting: drop-in/.git/objects/dc/deddba8e3961c5073bf981cf9a53c89b40a47f  
   creating: drop-in/.git/objects/b6/
 extracting: drop-in/.git/objects/b6/2522a3fdcdf96f4f919b11277f7337a70a6322  
 extracting: drop-in/.git/objects/b6/e3ec19e114d1678898ef2e497103f58c86097b  
   creating: drop-in/.git/objects/e1/
 extracting: drop-in/.git/objects/e1/4fa8ee268cf676fda534afc39474e944f25f6b  
   creating: drop-in/.git/objects/02/
 extracting: drop-in/.git/objects/02/6cba3e065d6da19b710b2d9f546285004b70f8  
 extracting: drop-in/.git/objects/02/1082a86c4b1e63cd8f2794667cc6d06824d617  
   creating: drop-in/.git/objects/71/
 extracting: drop-in/.git/objects/71/9265199609df93190155e726a96da05bb96822  
 extracting: drop-in/.git/objects/71/09f9026464ad55fdea2aab0a8e729c40722b73  
   creating: drop-in/.git/objects/6b/
 extracting: drop-in/.git/objects/6b/079b1ed7682583f38ad1730277a35d4f368639  
   creating: drop-in/.git/objects/b3/
 extracting: drop-in/.git/objects/b3/c71daf5e79b53c9eff00f6aa50bd7da5c1fd16  
 extracting: drop-in/.git/objects/b3/41ac7d93f998369a386ab4964bcb8439ba18bb  
   creating: drop-in/.git/objects/1c/
 extracting: drop-in/.git/objects/1c/f6962eb318cedc9828a447ba5eeb7097392780  
 extracting: drop-in/.git/objects/1c/8c00ade55094a39e636ba55bcd1a24be1f1343  
   creating: drop-in/.git/objects/4d/
 extracting: drop-in/.git/objects/4d/30ed3ba7393ec356c478c59ba3057e9ab1da96  
 extracting: drop-in/.git/objects/4d/7d455f2d8081bf0eb639bdaeb398aff5669b0b  
 extracting: drop-in/.git/objects/4d/64199b622de7d29fcfbe37e634e41ed58c0fa6  
   creating: drop-in/.git/objects/5b/
 extracting: drop-in/.git/objects/5b/df32ab626b650472658d913bd7710de0642744  
 extracting: drop-in/.git/objects/5b/fa5586af3292c29b8aeea10b1cbaa5fa88e8df  
 extracting: drop-in/.git/objects/5b/01229a11855ca14fee55218dcce7bf9a144bd5  
   creating: drop-in/.git/objects/ac/
 extracting: drop-in/.git/objects/ac/c2309e6ad2015dab5166c97ef4033db51d0a60  
   creating: drop-in/.git/objects/af/
 extracting: drop-in/.git/objects/af/385cefee52d53047f96b7e10dd1a785a15c647  
 extracting: drop-in/.git/objects/af/06162dc7bf59b04c0a85bb2edf923b187f9941  
   creating: drop-in/.git/objects/29/
 extracting: drop-in/.git/objects/29/4f30803047104bea8d80dccc2d137dd53a5a90  
   creating: drop-in/.git/objects/47/
 extracting: drop-in/.git/objects/47/caea4667f2be4aef66db3ff4e74e267f193f57  
 extracting: drop-in/.git/objects/47/0860d5eabbd9874cc286f160a61b87755f64ba  
   creating: drop-in/.git/objects/0a/
 extracting: drop-in/.git/objects/0a/af251322a7c71c2c0563ae965a4e722219cc76  
 extracting: drop-in/.git/objects/0a/e2112e90322e3f5dfc0197251708c68885244f  
   creating: drop-in/.git/objects/53/
 extracting: drop-in/.git/objects/53/69fe157d8f60295229eae31687b6b51efe0764  
   creating: drop-in/.git/objects/d3/
 extracting: drop-in/.git/objects/d3/f4ed0e761c89845e5c436ef07782185f952896  
   creating: drop-in/.git/objects/74/
 extracting: drop-in/.git/objects/74/f4a834835e53f878dcb94d774dd88749331f21  
 extracting: drop-in/.git/objects/74/2c6d841d3a1ebb89ffe0a3f5cc1da9e2a9b25a  
   creating: drop-in/.git/objects/4c/
 extracting: drop-in/.git/objects/4c/6a305916eb0ac4e1f281cfdc2c9d2cb3e8eda1  
   creating: drop-in/.git/objects/14/
 extracting: drop-in/.git/objects/14/fe848ca26388170b8275e8cb04f761fb6db797  
   creating: drop-in/.git/objects/22/
 extracting: drop-in/.git/objects/22/b0e6ec28b78e0c40f53d62b8fc53f215e83b14  
   creating: drop-in/.git/objects/6c/
 extracting: drop-in/.git/objects/6c/6ce598cb7a8d4a56405f663ea82266d4197c0e  
   creating: drop-in/.git/objects/d9/
 extracting: drop-in/.git/objects/d9/3c27af858c27fda36cf2cb24dc6b17ede1dc70  
   creating: drop-in/.git/objects/1a/
 extracting: drop-in/.git/objects/1a/561ac61d6b79f5995640a61dec902262e32e09  
   creating: drop-in/.git/objects/c5/
 extracting: drop-in/.git/objects/c5/3c3e0b575bfa83168b20d26c434816006663b2  
   creating: drop-in/.git/objects/44/
 extracting: drop-in/.git/objects/44/3ed121c5941dfe87079299ba10223c03d56946  
   creating: drop-in/.git/objects/98/
 extracting: drop-in/.git/objects/98/7bc7e8c1fc998483fc7ece99d1f7889aad14ae  
   creating: drop-in/.git/objects/45/
 extracting: drop-in/.git/objects/45/840ab1e860b83bf5ef6c434fbec4fd14f7fbab  
 extracting: drop-in/.git/objects/45/5a99a92c0a2cc12675c0cf8cab5762bb7dafae  
   creating: drop-in/.git/objects/f1/
 extracting: drop-in/.git/objects/f1/ee9881c5614b3e01695f1f9b74a8320d8d56fb  
   creating: drop-in/.git/objects/92/
 extracting: drop-in/.git/objects/92/9e3918bed4c8f3432c1f7c7ddfe5b378e177e1  
  inflating: drop-in/.git/index      
 extracting: drop-in/.git/COMMIT_EDITMSG  
   creating: drop-in/.git/logs/
  inflating: drop-in/.git/logs/HEAD  
   creating: drop-in/.git/logs/refs/
   creating: drop-in/.git/logs/refs/heads/
  inflating: drop-in/.git/logs/refs/heads/master
```

Nos movemos a la carpeta en la que vamos a estar trabajando y vemos su contenido ([[ls]] y cd).
```bash
AsumomezaC-picoctf@webshell:~/drop-in$ ls -la
total 4
drwxr-xr-x 3 AsumomezaC-picoctf AsumomezaC-picoctf  36 Mar 12  2024 .
drwxr-xr-x 3 AsumomezaC-picoctf AsumomezaC-picoctf  57 Feb 28 01:44 ..
drwxr-xr-x 8 AsumomezaC-picoctf AsumomezaC-picoctf 166 Mar 12  2024 .git
-rw-r--r-- 1 AsumomezaC-picoctf AsumomezaC-picoctf  22 Mar 12  2024 message.py
```

## Solución 1
Observamos los commits pasados.
```bash

commit 929e3918bed4c8f3432c1f7c7ddfe5b378e177e1 (HEAD -> master)
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:17 2024 +0000

    important business work

commit 5611f02bbfed52af8c78eb92ec58a323bebf96da
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:17 2024 +0000

    important business work

commit 455a99a92c0a2cc12675c0cf8cab5762bb7dafae
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:17 2024 +0000

    important business work

commit bd7c2f9c5d330be001284b360ef4702bc7883f9b
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:17 2024 +0000

    important business work

commit f1ee9881c5614b3e01695f1f9b74a8320d8d56fb
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:17 2024 +0000

    important business work

commit f89bbe15744eee2f55f7692e67e5f68687b66d61
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:17 2024 +0000

    important business work

commit 0ae2112e90322e3f5dfc0197251708c68885244f
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:17 2024 +0000

    important business work

commit dcdeddba8e3961c5073bf981cf9a53c89b40a47f
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:17 2024 +0000

    important business work

commit 32557fcd3e09bff7d3c656fda7f6e61e95af8dc7
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:17 2024 +0000

    important business work

commit 5b01229a11855ca14fee55218dcce7bf9a144bd5
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:17 2024 +0000

    important business work

commit 9f32cd1d5537bc51b9bb122d0631f0f7ea10f56b
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:17 2024 +0000

    important business work

commit 5fe66c5e92669f96192642b8ed04a5224c13d20a
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:17 2024 +0000

    important business work

commit a4331e45dcdf400d29bccc1712bd8ba107501db9
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:17 2024 +0000

    important business work

commit c3322454b6edc19d358e6b203c55d18e8b3f8fcb
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:17 2024 +0000

    important business work

commit 9944463a578521c39715bbd8b85cb33d5f18045e
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:17 2024 +0000

    important business work

commit e271500fc77eac9d2d4b00e4a80d0a9f6b676b61
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:17 2024 +0000

    important business work

commit 2fba0884f44ccbab33a550114114542029077ff8
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:17 2024 +0000

    important business work

commit 7a28ce3f6649f381149f8ab158fd11ee61a85603
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:17 2024 +0000

    important business work

commit 877703e7c4038a1a8f0f7e312309fe0128f8660a
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:17 2024 +0000

    important business work

commit 443ed121c5941dfe87079299ba10223c03d56946
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:17 2024 +0000

    important business work

commit f78a281620ddd2843ee1cde3877867d72ab25f19
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:17 2024 +0000

    important business work

...

commit 23e9d4ce78b3cea725992a0ce6f5eea0bf0bcdd4
Author: picoCTF{@sk_th3_1nt3rn_81e716ff} <ops@picoctf.com>
Date:   Tue Mar 12 00:07:15 2024 +0000

    optimize file size of prod code

commit 3ce5c692e2f9682a866c59ac1aeae38d35d19771
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:15 2024 +0000

    create top secret project
```
Al final encontramos que se encontraba el autor con el nombre de la bandera.

## Solución 2
Vemos que autores han realizado commits para buscar el culpable ([[ic/comunes/software/programación/Git#1️⃣ Ver una lista de autores y cantidad de commits]]).
```bash
AsumomezaC-picoctf@webshell:~/drop-in$ git shortlog -s -n --all

   501  picoCTF
     1  picoCTF{@sk_th3_1nt3rn_81e716ff}
```

Y vemos quien tiene un nombre bastante sospechoso.
## Respuesta
picoCTF{@sk_th3_1nt3rn_81e716ff}