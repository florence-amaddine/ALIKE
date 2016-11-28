# ALIKE
#!/bin/bash
clear
SERVER=$1;SERVER=${SERVER^^}
SIZE=${#SERVER}
Fil=`expr $SIZE - 3`
Inst=`expr $SIZE - 4`
Sit=`expr $SIZE - 5`
Cri=`expr $SIZE - 6`
Dmz=`expr $SIZE - 7`
echo;echo

DD=$(echo ${SERVER:$Dmz:1})

test $DD =  "Z" &&  DD="YES" || DD="NO"
test $DD =  "YES" &&  PrEnvFin=`expr $SIZE - 9 ` || PrEnvFin=`expr $SIZE - 8`

export ProdEnv=$(echo ${SERVER:2:$PrEnvFin})
export Prod=$(echo ${SERVER:2:2})
export TRS=$(echo ${SERVER:0:1})
export OSV=$(echo ${SERVER:1:1})
#export ENVR
export CRIT=$(echo ${SERVER:$Cri:1})
ST=$(echo ${SERVER:$Sit:1})
#-------------------------------------------------------------------------------------------
Produit()
{
case ${Prod} in
        AP) ENVR=${ProdEnv:3};CODE="APP ======>";PRODUIT=APPLIANCE ;;
        BA) ENVR=${ProdEnv:5};CODE="BATCH ====>";PRODUIT=BATCH ;;
        NN) ENVR=${ProdEnv:2};CODE="NN =======>";PRODUIT="Big DATA Name Node" ;;
        EN) ENVR=${ProdEnv:2};CODE="EN =======>";PRODUIT="Big DATA Edge Node" ;;
        DN) ENVR=${ProdEnv:2};CODE="DN =======>";PRODUIT="Big DATA Data Node" ;;
        DO) ENVR=${ProdEnv:6};CODE="DOMINO =======>";PRODUIT="Application DOMINO" ;;
        EX) ENVR=${ProdEnv:7};CODE="EXALEAD =======>";PRODUIT="LOGICIEL EXALEAD" ;;
        EC) ENVR=${ProdEnv:4};CODE="ECSH =======>";PRODUIT="LOGICIEL ELASTIC SEARCH" ;;
        TC) ENVR=${ProdEnv:3};CODE="TCO =======>";PRODUIT="LOGICIEL TRUESIGHT CAPACITY" ;;
        IL) ENVR=${ProdEnv:4};CODE="ILMT =======>";PRODUIT="LOGICIEL LICENSING Capacité IBM" ;;
        GP) ENVR=${ProdEnv:3};CODE="GPO =======>";PRODUIT="PROJET GPO" ;;
        J2) ENVR=${ProdEnv:4};CODE="J2EE ======>";PRODUIT="APACHE / TOMCAT" ;;
        LA) ENVR=${ProdEnv:3};CODE="LAB =======>";PRODUIT="TESTS / VALIDATIONS DEI" ;;
        LD) ENVR=${ProdEnv:4};CODE="LDAP =======>";PRODUIT="AUTHENTIFICATION LDAP" ;;
        MQ) ENVR=${ProdEnv:2};CODE="MQ =======>";PRODUIT="MQSERIES" ;;
        NT) ENVR=${ProdEnv:6};CODE="NTIERS =======>";PRODUIT="EQUIPE NTIERS" ;;
        PH) ENVR=${ProdEnv:3};CODE="PHP =======>";PRODUIT="APPLICATION PHP (SPIP/DRUPAL)" ;;
        SA) ENVR=${ProdEnv:3};CODE="SAS =======>";PRODUIT="SAS DE LIVRAISON DEI" ;;
        SG) ENVR=${ProdEnv:4};CODE="SGBD =======>";PRODUIT="BASES DE DONNEES " ;;
        SH) ENVR=${ProdEnv:4};CODE="SHAR =======>";PRODUIT="PARTAGE DE REPERTOIRES NFS/SMBFS" ;;
        SY) ENVR=${ProdEnv:3};CODE="SYS =======>";PRODUIT="EQUIPE SYSTEME" ;;
        WE) ENVR=${ProdEnv:3};CODE="WEB =======>";PRODUIT="APPLICATIONS WEBSPHERE" ;;
        PA) ENVR=${ProdEnv:3};CODE="PAT =======>";PRODUIT="PATROL" ;;
        SU) ENVR=${ProdEnv:3};CODE="SUP =======>";PRODUIT="SUPERVISION" ;;
        KV) ENVR=${ProdEnv:3};CODE="KVM =========>";PRODUIT="HYPERVISEUR DE TYPE KVM" ;;
        CT) ENVR=${ProdEnv:3};CODE="CTM =========>";PRODUIT="CONTROLM" ;;
        CA) ENVR=${ProdEnv:3};CODE="CAP ==========>";PRODUIT="CAPTURE" ;;
        3S) ENVR=${ProdEnv:2};CODE="3S ==========>";PRODUIT="3S SECURITé" ;;
        EA) ENVR=${ProdEnv:3};CODE="EAI =======>";PRODUIT="EAI" ;;
        ME) ENVR=${ProdEnv:5};CODE="METRO =======>";PRODUIT="METROLOGIE" ;;
        PA) ENVR=${ProdEnv:4};CODE="PAAS =======>";PRODUIT="ADMIN DU CLOUD" ;;
        IN) ENVR=${ProdEnv:4};CODE="INST =======>";PRODUIT="INSTALLATION" ;;
        GA) ENVR=${ProdEnv:4};CODE="GATE =======>";PRODUIT="ACCES SSH pour l'ADMINISTRATION" ;;
        WI) ENVR=${ProdEnv:4};CODE="WIKI =======>";PRODUIT="MEDIAWIKI, DOKUWIKI" ;;
        *) echo " Produit non identifier !!!";;
esac
}
#-----------------------------------------------------------------------------------------------
Trigramme_Service()
{
case ${TRS} in
        D) TRS="D ===========>  DEI / DPI" ;;
        I) TRS="I ===========>  IPSEC" ;;
        N) TRS="N ===========>  INPI" ;;
        *) echo " Trigramme Service non identifier !!!";;
esac
}
#-----------------------------------------------------------------------------------------------
OS()
{
case ${OSV} in
        A) OSV="A ===========>  AIX" ;;
        E) OSV="E ===========>  ESX" ;;
        L) OSV="L ===========>  LINUX" ;;
        K) OSV="K ===========>  KVM" ;;
        C) OSV="C ===========>  CLOUD" ;;
        B) OSV="B ===========>  BIG DATA" ;;
        *) echo " OS non identifier !!!";;
esac
}
#-----------------------------------------------------------------------------------------------
Environement()
{
case ${ENVR} in
        BAC) ENVR="BAC ===========>  Bac à sable" ;;
        BENCH) ENVR="BENCH ===========>  Serveur générant/analysant de la charge applicative" ;;
        DEV) ENVR="DEV ===========>  Developpement" ;;
        DRP) ENVR="DRP ===========>  Developpement, Recette, Pre-exploitation" ;;
        FORM) ENVR="FORM ===========>  Formation" ;;
        INT) ENVR="INT ===========>  Integration" ;;
        IR) ENVR="IR ===========>  Integration et Recette" ;;
        RA) ENVR="RA ===========>  Reprise d'antiriorité" ;;
        REC) ENVR="REC =========>  Recette" ;;
        SIMU) ENVR="SIMU ===========>  Simulation" ;;
        TEC) ENVR="TEC ===========>  Technique" ;;
        TEST) ENVR="TEST ===========>  Tests" ;;
        VA) ENVR="VA ===========>  Validation" ;;
        *) echo " Environement non identifier !!!";;
esac
}
#----------------------------------------------------------------------------------------------
CRITICIT()
{
case ${CRIT} in
        D) CRIT="D ===========>  P0 ou Critique" ;;
        C) CRIT="C ===========>  P1 ou Critique" ;;
        A) CRIT="A ===========>  P2 ou Sensible" ;;
        I) CRIT="I ===========>  Initiale (ASI)" ;;
        Y) CRIT="Y ===========>  Initiale hors ASI (DPI)" ;;
        RA) CRIT="RA ===========>  Raspberry PI (mission sec pot de miel)" ;;

        *) echo " OS non identifier !!!";;
esac
}
#----------------------------------------------------------------------------------------------
SITE()
{
case ${ST} in
        0) ST="0 ===========>  Pas de site particulier" ;;
        1) ST="1 ===========>  Arcueil 1" ;;
        2) ST="2 ===========>  Arcueil 2" ;;
        3) ST="3 ===========>  Arcueil 3 => PROD" ;;
        4) ST="4 ===========>  Arcueil 4" ;;
        5) ST="5 ===========>  PSI " ;;
        6) ST="6 ===========>  Bordeaux" ;;
        *) echo " Site non identifier !!!";;
esac
}
#----------------------------------------------------------------------------------------------
Trigramme_Service
Produit
OS
Environement
CRITICIT
SITE

echo;echo
echo "Informations du serveur $1 "
echo
echo " Trigramme Service : " $TRS
echo " OS                : " $OSV
echo " Produit           : " $CODE    $PRODUIT
echo " Environement      : " $ENVR
echo " DMZ ?             : " $DD
echo " Criticité         : " $CRIT
echo " Numéro de Site    : " $ST
echo " Numéro Instance   : " $(echo ${SERVER:$Inst:1})
echo " Filière           : " $(echo ${SERVER:$Fil:3})
echo;echo

exit 0
