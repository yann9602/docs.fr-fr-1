---
title: "Guide de d&#233;ploiement du .NET Framework pour les administrateurs | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "guide de l'administrateur, déployer .NET Framework"
  - "déploiement (.NET Framework), guide de l'administrateur"
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
caps.latest.revision: 40
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 38
---
# Guide de d&#233;ploiement du .NET Framework pour les administrateurs
Cet article explique étape par étape comment un administrateur système peut déployer [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] et ses dépendances système dans un réseau à l'aide de Microsoft System Center Configuration Manager \(SCCM\).  Cet article suppose que tous les ordinateurs clients cibles ont la configuration minimale requise pour le .NET Framework.  Pour obtenir la liste des configurations logicielle et matérielle requises pour installer le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], consultez [Configuration requise](../../../docs/framework/get-started/system-requirements.md).  
  
> [!NOTE]
>  Les logiciels référencés dans ce document, y compris, mais de manière non limitative, le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], System Center Configuration Manager et Active Directory, sont tous soumis à des termes et conditions de contrat de licence.  Les présentes instructions supposent que lesdits termes et conditions du contrat de licence ont été passés en revue et acceptés par les propriétaires de licences des logiciels concernés.  Ces instructions ne remplacent pas les termes et conditions desdits contrats de licence.  
>   
>  Pour plus d'informations sur la prise en charge du .NET Framework, voir [Politique de support \(Support Lifecycle Policy\) pour Microsoft .NET Framework](http://go.microsoft.com/fwlink/?LinkId=196607) sur le site web Aide et Support de Microsoft.  
  
 Cette rubrique contient les sections suivantes :  
  
 [Processus de déploiement](#the_deployment_process)   
 [Déployer le .NET Framework](#deploying_in_a_test_environment)  
 [Créer un regroupement](#creating_a_collection)  
 [Créer un package et un programme](#creating_a_package)  
 [Sélectionner un point de distribution](#select_dist_point)  
 [Déployer le package](#deploying_package)  
 [Ressources](#resources)  
 [Résolution des problèmes](#troubleshooting)  
  
<a name="the_deployment_process"></a>   
## Processus de déploiement  
 Lorsque l'infrastructure de prise en charge est en place, utilisez System Center 2012 Configuration Manager pour déployer le package redistribuable .Net Framework sur les ordinateurs du réseau.  Générer l'infrastructure implique la création et la définition de cinq éléments principaux : les regroupements, un package et un programme pour les logiciels, des points de distribution et des déploiements.  
  
-   Les **regroupements** sont des ensembles de ressources de Configuration Manager, tels que des utilisateurs, des groupes d'utilisateurs ou des ordinateurs, sur lesquels le .Net Framework est déployé.  Pour plus d'informations, voir [Regroupements dans Configuration Manager](http://technet.microsoft.com/library/gg682169.aspx) dans la bibliothèque de la documentation Configuration Manager.  
  
-   Les **packages et programmes** sont généralement les applications logicielles à installer sur un ordinateur client, mais ils peuvent également contenir des fichiers individuels, des mises à jour, ou même des commandes individuelles.  Pour plus d'informations, voir [Packages et programmes dans Configuration Manager](http://technet.microsoft.com/library/gg699369.aspx) dans la bibliothèque de la documentation Configuration Manager.  
  
-   Les **points de distribution** sont des rôles de système de site Configuration Manager qui stockent les fichiers requis pour l'exécution des logiciels sur les ordinateurs clients.  Lorsque le client Configuration Manager reçoit et traite un déploiement de logiciel, il contacte un point de distribution pour télécharger le contenu associé au logiciel et démarrer le processus d'installation.  Pour plus d'informations, voir [Présentation de la gestion de contenu dans Configuration Manager](http://technet.microsoft.com/library/gg682083.aspx) dans la bibliothèque de la documentation Configuration Manager.  
  
-   Les **déploiements** instruisent les membres applicables du regroupement cible spécifié pour installer le package logiciel.  Pour plus d'informations, voir [Comment déployer des applications dans Configuration Manager](http://technet.microsoft.com/library/gg682082.aspx) dans la bibliothèque de la documentation Configuration Manager.  
  
> [!IMPORTANT]
>  Les procédures de cette rubrique contiennent les paramètres classiques pour créer et déployer un package et un programme, et ne couvrent pas tous les paramètres possibles.  Pour connaître les autres options de déploiement disponibles dans Configuration Manager, voir la [bibliothèque de la documentation Configuration Manager](http://technet.microsoft.com/library/gg682041.aspx).  
  
<a name="deploying_in_a_test_environment"></a>   
## Déployer le .NET Framework  
 Vous pouvez utiliser System Center 2012 Configuration Manager pour déployer une installation sans assistance de [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], pour laquelle les utilisateurs n'interagissent pas avec le processus d'installation.  Procédez comme suit :  
  
1.  [Créez un regroupement](#creating_a_collection).  
  
2.  [Créez un package et un programme pour le package redistribuable .Net Framework](#creating_a_package).  
  
3.  [Sélectionnez un point de distribution](#select_dist_point).  
  
4.  [Déployez le package](#deploying_package).  
  
<a name="creating_a_collection"></a>   
### Créer un regroupement  
 Dans cette étape, sélectionnez les ordinateurs sur lesquels seront déployés le package et le programme, et regroupez\-les dans un regroupement de périphériques.  Pour créer un regroupement dans Configuration Manager, utilisez des règles d'adhésion directes \(où les membres du regroupement sont spécifiés manuellement\) ou des règles de requête \(où Configuration Manager détermine les membres du regroupement selon des critères que vous avez spécifiés\).  Pour plus d'informations sur les règles d'adhésion, notamment les règles directes et les requêtes, voir [Introduction aux regroupements dans Configuration Manager](http://technet.microsoft.com/library/gg682177.aspx) dans la bibliothèque de la documentation Configuration Manager.  
  
 Pour créer un regroupement :  
  
1.  Dans la Console Configuration Manager, choisissez **Ressources et Conformité**.  
  
2.  Dans l'espace de travail **Ressources et Conformité**, choisissez **Regroupements de périph.**  
  
3.  Sous l'onglet **Accueil** dans le groupe **Créer**, choisissez **Créer un regroupement de périphériques**.  
  
4.  Dans la page **Général** de l'**Assistant Création d'un regroupement de périphériques**, entrez un nom du regroupement.  
  
5.  Choisissez **Parcourir** pour spécifier une limitation au regroupement.  
  
6.  Dans la page **Règles d'adhésion**, choisissez **Ajouter une règle**, puis **Règle directe** pour ouvrir l'**Assistant Création d'une règle d'adhésion directe**.  Sélectionnez **Suivant**.  
  
7.  Dans la page **Rechercher des ressources**, dans la liste **Classe de ressource**, choisissez **Ressource système**.  Dans la liste **Nom de l'attribut**, choisissez **Nom**.  Dans le champ **Valeur**, entrez `%` et choisissez **Suivant**.  
  
8.  Dans la page **Sélectionner les ressources**, cochez la case de chaque ordinateur sur lequel vous souhaitez déployer .Net Framework.  Choisissez **Suivant**, puis terminez l'Assistant.  
  
9. Dans la page **Règles d'adhésion** de l'**Assistant Création d'un regroupement de périphériques**, choisissez **Suivant**, puis terminez l'Assistant.  
  
 Pour plus d'informations sur les regroupements, voir [Regroupements dans Configuration Manager](http://technet.microsoft.com/library/bb693730.aspx) dans la bibliothèque de la documentation Configuration Manager.  
  
<a name="creating_a_package"></a>   
### Créer un package et un programme pour le package redistribuable .Net Framework  
 Les étapes suivantes permettent de créer manuellement un package pour le package redistribuable .NET Framework.  Le package contient les paramètres spécifiés pour l'installation du .Net Framework et l'emplacement à partir duquel le package sera distribué aux ordinateurs cibles.  
  
 Pour créer un package :  
  
1.  Dans la Console Configuration Manager, choisissez **Bibliothèque de logiciels**.  
  
2.  Dans l'espace de travail **Bibliothèque de logiciels**, développez **Gestion des applications**, puis choisissez **Packages**.  
  
3.  Sous l'onglet **Accueil**, dans le groupe **Créer**, choisissez **Créer un package**.  
  
4.  Dans la page **Package** de l'**Assistant Création d'un package et d'un programme**, entrez les informations suivantes :  
  
    -   Nom : `.Net Framework 4.5`  
  
    -   Fabricant : `Microsoft`  
  
    -   Langue :  `Anglais (US)`  
  
5.  Choisissez **Ce package contient des fichiers source**, puis **Parcourir** pour sélectionner le dossier local ou réseau qui contient les fichiers d'installation de .Net Framework.  Lorsque vous avez sélectionné le dossier, choisissez **OK**, puis **Suivant**.  
  
6.  Dans la page **Type de programme** de l'Assistant, choisissez **Programme standard**, puis **Suivant**.  
  
7.  Dans la page **Programme** de l'**Assistant Création d'un package et d'un programme**, entrez les informations suivantes :  
  
    1.  **Nom :** `.Net Framework 4.5`  
  
    2.  **Ligne de commande :** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` \(les options de ligne de commande sont décrites dans le tableau après ces étapes\)  
  
    3.  **Exécuter :** choisissez **Masqué**.  
  
    4.  **Le programme peut s'exécuter :** sélectionnez l'option qui spécifie que le programme peut s'exécuter que l'utilisateur soit connecté ou non.  
  
8.  Dans la page **Spécifications**, acceptez les valeurs par défaut en choisissant **Suivant**, puis terminez l'Assistant.  
  
 Le tableau suivant décrit les options de ligne de commande spécifiées dans l'étape 7.  
  
|Option|Description|  
|------------|-----------------|  
|**\/q**|Définit le mode silencieux.  Aucune entrée d'utilisateur n'est requise, et aucun résultat n'est affiché.|  
|**\/norestart**|Empêche le programme d'installation de redémarrer automatiquement.  Si vous utilisez cette option, Configuration Manager doit gérer le redémarrage de l'ordinateur.|  
|**\/chainingpackage** *PackageName*|Spécifie le nom du package qui effectue le chaînage.  Ces informations sont stockées avec d'autres informations de session d'installation pour les personnes inscrites au [Programme d'amélioration du produit Microsoft \(CEIP\)](http://go.microsoft.com/fwlink/p/?LinkId=248244).  Si le nom du package inclut des espaces, utilisez des guillemets doubles comme délimiteurs ; par exemple: **\/chainingpackage "Chaining Product"**.|  
  
 Les étapes suivantes créent un package nommé .Net Framework 4.5.  Le programme déploie une installation sans assistance de .Net Framework 4.5.  Dans une installation sans assistance, les utilisateurs n'interagissent pas avec le processus d'installation et l'application de chaînage doit capturer le code de retour et gérer le redémarrage ; consultez la page [Obtention d'informations de progression d'un package d'installation](http://go.microsoft.com/fwlink/?LinkId=179606) dans MSDN Library.  
  
<a name="select_dist_point"></a>   
### Sélectionner un point de distribution  
 Pour distribuer le package et le programme aux ordinateurs clients à partir d'un serveur, vous devez d'abord désigner un système de site comme un point de distribution, puis distribuer le package au point de distribution.  
  
 Utilisez les étapes suivantes pour sélectionner un point de distribution pour le package de .Net Framework 4.5 créé au cours la section précédente :  
  
1.  Dans la Console Configuration Manager, choisissez **Bibliothèque de logiciels**.  
  
2.  Dans l'espace de travail **Bibliothèque de logiciels**, développez **Gestion des applications**, puis choisissez **Packages**.  
  
3.  Dans la liste de packages, sélectionnez le package **.Net Framework 4.5** créé dans la section précédente.  
  
4.  Sous l'onglet de **Accueil**, dans le groupe **Déploiement**, choisissez **Distribuer du contenu**.  
  
5.  Sous l'onglet **Général** de l'**Assistant Distribuer du contenu**, choisissez **Suivant**.  
  
6.  Dans la page **Destination du contenu** de l'Assistant, choisissez **Ajouter**, puis **Point de distribution**.  
  
7.  Dans la boîte de dialogue **Ajouter des points de distribution**, sélectionnez les points de distribution qui hébergeront le package et le programme, puis choisissez **OK**.  
  
8.  Terminez l'Assistant.  
  
 Le package contient désormais toutes les informations nécessaires au déploiement sans assistance de .Net Framework 4.5.  Avant de déployer le package et le programme, vérifiez qu'il a été installé sur le point de distribution ; consultez la section « Surveiller le contenu » de la page [Opérations et maintenance de la gestion de contenu dans Configuration Manager](http://technet.microsoft.com/library/gg712694.aspx#BKMK_MonitorContent) dans la bibliothèque de la documentation Configuration Manager.  
  
<a name="deploying_package"></a>   
### Déployer le package  
 Pour déployer le package et le programme .Net Framework 4.5 :  
  
1.  Dans la Console Configuration Manager, choisissez **Bibliothèque de logiciels**.  
  
2.  Dans l'espace de travail **Bibliothèque de logiciels**, développez **Gestion des applications**, puis choisissez **Packages**.  
  
3.  Dans la liste des packages, sélectionnez le package que vous avez créé, appelé **.Net Framework 4.5**.  
  
4.  Sous l'onglet **Accueil**, dans le groupe **Déploiement**, choisissez **Déployer**.  
  
5.  Dans la page **Général** de l'**Assistant Déploiement logiciel**, choisissez **Parcourir**, puis sélectionnez le regroupement créé précédemment.  Sélectionnez **Suivant**.  
  
6.  Dans la page **Contenu** de l'Assistant, vérifiez que le point à partir duquel vous souhaitez distribuer le logiciel s'affiche, puis choisissez **Suivant**.  
  
7.  Dans la page **Paramètres de déploiement** de l'Assistant, assurez\-vous que **Action** est défini sur **Installer**, et **Objectif** sur **Requis**.  Cela garantit que le package logiciel est une installation obligatoire sur les ordinateurs ciblés.  Sélectionnez **Suivant**.  
  
8.  Dans la page **Planification** de l'Assistant, spécifiez à quel moment vous souhaitez que .Net Framework soit installé.  Choisissez **Nouveau** pour déterminer le moment de l'installation, ou demandez au logiciel d'effectuer l'installation lorsque l'utilisateur se connecte ou se déconnecte, ou dès que possible.  Sélectionnez **Suivant**.  
  
9. Dans la page **Expérience utilisateur** de l'Assistant, utilisez les valeurs par défaut et choisissez **Suivant**.  
  
    > [!WARNING]
    >  Il est possible que votre environnement de production ait des stratégies qui requièrent des sélections différentes pour la planification de déploiement.  Pour plus d'informations sur ces options, voir [Propriétés du nom de la publication : Onglet Calendrier](http://technet.microsoft.com/library/bb694016.aspx) dans la bibliothèque TechNet.  
  
10. Dans la page **Points de distribution** de l'Assistant, utilisez les valeurs par défaut et choisissez **Suivant**.  
  
11. Terminez l'Assistant.  Vous pouvez surveiller la progression du déploiement dans le nœud **Déploiements** de l'espace de travail **Contrôle**.  
  
 Le package est déployé dans le regroupement ciblé et l'installation sans assistance de .Net Framework 4.5 peut commencer.  Pour plus d'informations sur les codes d'erreur liés à l'installation de .NET Framework 4.5, consultez la section [Codes de retour](#return_codes) plus loin dans cette rubrique.  
  
<a name="resources"></a>   
## Ressources  
 Pour plus d'informations sur l'infrastructure pour tester le déploiement du package redistribuable [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], consultez les ressources suivantes.  
  
 **Active Directory, DNS, DHCP :**  
  
-   [Services de domaine Active Directory pour Windows Server 2008](http://technet.microsoft.com/library/dd378891.aspx)  
  
-   [Guide pas à pas Windows Server 2008 pour DNS dans les réseaux de petite taille](http://www.microsoft.com/download/details.aspx?id=17157)  
  
-   [Serveur DNS](http://technet.microsoft.com/library/cc732997.aspx)  
  
-   [Serveur DHCP](http://technet.microsoft.com/library/cc896553.aspx)  
  
 **SQL Server 2008 :**  
  
-   [Installation de SQL Server 2008 \(vidéo liée à SQL Server\)](http://technet.microsoft.com/library/dd299415.aspx)  
  
-   [Vue d'ensemble de la sécurité SQL Server 2008 pour les administrateurs de base de données](http://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)  
  
 **System Center 2012 Configuration Manager \(point de gestion, point de distribution\) :**  
  
-   [Administration de site pour System Center 2012 Configuration Manager](http://technet.microsoft.com/library/gg681983.aspx)  
  
-   [Planification et déploiement d'un site Configuration Manager unique](http://technet.microsoft.com/library/bb680961.aspx)  
  
 **Client System Center 2012 Configuration Manager pour des ordinateurs Windows :**  
  
-   [Déploiement de clients pour System Center 2012 Configuration Manager](http://technet.microsoft.com/library/gg699391.aspx)  
  
<a name="troubleshooting"></a>   
## Résolution des problèmes  
  
### Emplacements des fichiers journaux  
 Les fichiers journaux suivants sont générés pendant l'installation du [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] :  
  
 %temp%\\Microsoft .NET Framework 4.5\*.txt                                 
 %temp%\\Microsoft .NET Framework 4.5\*.html  
  
 Vous pouvez utiliser l'[outil de collecte des journaux](http://www.microsoft.com/download/details.aspx?id=12493) pour collecter les fichiers journaux [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] et créer un fichier CAB compressé \(.cab\) afin de réduire la taille des fichiers.  
  
<a name="return_codes"></a>   
### Codes de retour  
 Le tableau suivant répertorie les codes de retour les plus courants pour le programme d'installation du package redistribuable [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].  Les codes de retour sont identiques pour toutes les versions du programme d'installation.  
  
 Pour plus d'informations, voir la section suivante : [Codes d'erreur de téléchargement](#additional_error_codes).  
  
|Code de retour|Description|  
|--------------------|-----------------|  
|0|Installation terminée.|  
|1602|L'utilisateur a annulé l'installation.|  
|1603|Une erreur irrécupérable s'est produite pendant l'installation.|  
|1641|Un redémarrage est nécessaire pour terminer l'installation.  Ce message indique que l'opération a réussi.|  
|3010|Un redémarrage est nécessaire pour terminer l'installation.  Ce message indique que l'opération a réussi.|  
|5100|L'ordinateur de l'utilisateur n'a pas la configuration requise.|  
  
<a name="additional_error_codes"></a>   
### Codes d'erreur de téléchargement  
  
-   [Codes d'erreur du service de transfert intelligent en arrière\-plan \(BITS\)](http://msdn.microsoft.com/library/aa362823.aspx)  
  
-   [Codes d'erreur du moniker d'URL](http://msdn.microsoft.com/library/ms775145.aspx)  
  
-   [Codes d'erreur WinHttp](http://msdn.microsoft.com/library/aa383770.aspx)  
  
 Autres codes d'erreur :  
  
-   [Codes d'erreur Windows Installer](http://msdn.microsoft.com/library/aa368542.aspx)  
  
-   [Codes de résultat de l'Agent de mise à jour automatique Windows Update](http://technet.microsoft.com/library/cc720442.aspx)  
  
## Voir aussi  
 [Guide de déploiement pour les développeurs](../../../docs/framework/deployment/deployment-guide-for-developers.md)   
 [Configuration requise](../../../docs/framework/get-started/system-requirements.md)