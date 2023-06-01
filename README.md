# Projekti nga lenda Machine Learning: Parashikimi i Ndryshimit të Punës
------------------------------------------------------

Projekti ka për bazë dataset-in HR Analytics - Job Change of Data Scientist.
Dataset-i është marrë i gatshem në Kaggle dhe përmban të dhëna rreth personave të cilët janë të punësuar në fushën e IT, më saktësisht në fushën e Data Science. Eshtë i dizajnuar ashtu që të kuptohen më lehtë faktorët të cilët shtyjnë punëtoret e kësaj fushe të ndërrojnë punën, gjë që ndihmon shumë sektorin e burimeve njerëzore.

Modeli i cili përdorë demografinë dhe eksperiencën, ndihmon në parashikimin e probabilitetit se cili nga kandidatët e vlerësuar për punesim ka tendencë të kerkojë ndërrim të kompanisë në një kohë më të shkurtë.

Dataset-i është i pabalancuar dhe shumica e vetive janë kategorike (nominal, ordinal, binary), ku disa kanë kardinalitet të lartë.

### Përshkrimi i Datasetit

Dataseti përmban informacione rreth kandidatëve për punë, duke përfshirë të dhëna demografike, arsimin, përvojën e punës, detaje të kompanisë dhe faktorë të tjerë të rëndësishëm.

1.  `enrollee_id`: Identifikues unik për çdo kandidat për punë.
2.  `city`: Kodi i qytetit ku ndodhet kandidati.
3.  `city_development_index`: Indeksi i zhvillimit të qytetit ku ndodhet kandidati.
4.  `gender`: Gjinia e kandidatit.
5.  `relevent_experience`: Përvoja e rëndësishme e kandidatit (ka përvojë të rëndësishme ose nuk ka përvojë të rëndësishme).
6.  `enrolled_university`: Lloji i orarit në universitet.
7.  `education_level`: Niveli më i lartë i arsimit i arritur nga kandidati.
8.  `major_discipline`: Disiplina kryesore e kandidatit.
9.  `experience`: Përvoja e punës në vite.
10. `company_size`: Madhësia e kompanisë ku kandidati është aktualisht i punësuar.
11. `company_type`: Lloji i kompanisë ku kandidati është aktualisht i punësuar.
12. `last_new_job`: Diferenca në vite midis punës së tanishme dhe punës së mëparshme.
13. `training_hours`: Orët e trajnimit të kryera nga kandidati.
14. `target`: Variabël që tregon nëse kandidati ka probabilitet të ndryshojë punë (0 = Nuk kërkon ndryshim të punës, 1 = Kërkon ndryshim të punës).

### Zhvillimi i Projektit

Notebook-u përmban kodin për të gjithë projektin, i ndarë në seksione të ndryshme. Këtu është një përmbledhje e hapave kryesorë të përfshirë:

1.  Ngarkimi dhe eksplorimi i të dhënave:

    -   Dataseti ngarkohet në një DataFrame të Pandas duke përdorur funksionin `read_csv()`.
    -   Të dhënat e disa rreshtave të para të datasetit shfaqen duke përdorur funksionin `head()`.
    -   Kryhen operacione eksploruese të ndryshme, si kontrolli i formës së datasetit dhe vlerave unike në kolonat specifike.

2.  Përpunimi i të dhënave:

    -   Kryhen hapat e pastrimit dhe përpunimit të të dhënave për të trajtuar vlerat e humbura dhe transformuar tiparet kategorike në paraqitje numerike.
    -   Tiparet kategorike mbushen me vlerën modë, ndërsa tiparet ordinalë enkodohen duke përdorur kategoritë e dhëna ordinalë.
    -   Kryhet shkallëzimi i tipareve numerike duke përdorur StandardScaler nga skit-learn.
    -   Variabla e synuar enkodohet si numra të plotë.
    -   Tiparet nominale enkodohen me one-hot encoding duke përdorur pd.get_dummies().

3.  Trajnimi dhe vlerësimi i modelit:

    -   Dataseti ndahet në pjesën e trajnimit dhe pjesën e testimi duke përdorur funksionin train_test_split().
    -   Inicializohet Klasifikuesi Random Forest, trajnohet në pjesën e trajnimit dhe përdoret për të bërë parashikime në pjesën e testimi.
    -   Llogaritet saktesia, matrica e konfuzionit dhe raporti i klasifikimit për të vlerësuar performancën e modelit.

4.  Model Tuning dhe krahasimi i modeleve:

    -   Përdoret GridSearchCV për të kryer një kërkim të hiperparametrave për Klasifikuesin Random Forest.
    -   Merrin hiperparametrat më të mira dhe përdoren për të trajnuar një Klasifikues të ri Random Forest.
    -   Modeli i perfeksionuar vlerësohet duke përdorur validim të kryqëzuar dhe krahasohet me klasifikues të tjerë, si Regresioni Logjistik, K-Neighbor më të Afërt, Mbështetësi i Vektorëve, dhe Rrjetat Neuronale.
    -   Llogariten dhe shfaqen metrikat e performancës (saktesia, matrica e konfuzionit, raporti i klasifikimit) për secilin klasifikues.

### Ekzekutimi

Për të ekzekutuar kodin dhe riprodhuar rezultatet, ju lutemi ndiqni këto hapa:

1.  Instaloni libraritë e nevojshme: pandas, scikit-learn dhe numpy.
2.  Sigurohuni që file "data_analisys.ipynb" gjendet në shtegun e njejtë me folder-in "Data".
3.  Hapni Notebook-un dhe ekzekutoni secilën qelizë në rradhë për të ekzekutuar kodin hapi pas hapi.

### Rezultatet

Projekti përdor disa klasifikues për të parashikuar ndryshimin e punës bazuar në datasetin e dhënë. Këtu janë rezultatet e arritura nga klasifikuesi Random Forest (Tuned), së bashku me klasifikuesit e tjerë për krahasim:

1.  Random Forest (Tuned):

    -   Saktesia: 0.7745
    -   Confusion Matrix:
    
        [[2583  297]
    
        [ 567  385]]


![image](https://github.com/PuhizaDoci/machine-learning/assets/44654048/7c84be6e-a3ee-4d44-b42c-c9df88bc8240)


2.  Random Forest:

    -   Saktesia: 0.7648
    -  Confusion Matrix:
        
        [[2574  306]
        
        [ 595  357]]

![image](https://github.com/PuhizaDoci/machine-learning/assets/44654048/03d49eb6-a64a-4e8c-b0c7-d8714a331259)


3.  Logistic Regression:

    -   Saktesia: 0.7656
    -   Confusion Matrix:
        
        [[2624  256]
 
        [ 642  310]]

![image](https://github.com/PuhizaDoci/machine-learning/assets/44654048/87e9a454-341e-46ef-86d2-c15fdb0e89f4)


4.  K-Nearest Neighbors:

    -   Saktesia: 0.7056
    -   Confusion Matrix:
        
        [[2577  303]
        
        [ 825  127]]
        
![image](https://github.com/PuhizaDoci/machine-learning/assets/44654048/589fdb59-6da4-45ba-b4f9-37d2c61cbb68)


5.  Support Vector Machines:

    -   Saktesia: 0.7515
    -   Confusion Matrix:
        
        [[2880    0]
        
        [ 952    0]]
        
![image](https://github.com/PuhizaDoci/machine-learning/assets/44654048/3763b62a-fd8f-46d9-af0c-af805264b7ad)


6.  Neural Networks:

    -   Saktesia: 0.7523
    -   Confusion Matrix:
        
        [[2858   22]
        
        [ 927   25]]

![image](https://github.com/PuhizaDoci/machine-learning/assets/44654048/8be144fe-056a-4664-b9c7-b4a1095a6ada)


Rezultatet tregojnë performancën e klasifikuesve të ndryshëm në parashikimin e ndryshimit të punës bazuar në datasetin e dhënë. Klasifikuesi Random Forest (Tuned) arriti saktesinë më të lartë në mesin e modeleve të vlerësuara.

Shënim: Rezultatet e arritura mund të ndryshojnë pak në vlerë, duke pasur parasysh natyrën e rastësishme të disa algoritmeve ose përdorimin e përshtatjes së hiperparametrave.
