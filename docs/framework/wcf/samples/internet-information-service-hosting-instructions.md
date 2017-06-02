---
title: "Instructions relatives &#224; l&#39;h&#233;bergement dans les Services Internet (IIS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
caps.latest.revision: 30
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 30
---
# Instructions relatives &#224; l&#39;h&#233;bergement dans les Services Internet (IIS)
Pour exécuter les exemples hébergés par les services IIS \(Internet Information Services\), vous devez vous assurer que les services IIS sont correctement installés et en cours d'exécution.  
  
### Pour installer IIS version 7.5 sur Windows Server 2008 R2  
  
1.  Dans **Gestionnaire de serveur**, sélectionnez **Rôles**. Sous **Résumé des rôles**, cliquez sur **Ajouter des rôles**.  
  
2.  Cliquez sur **Suivant** pour afficher la boîte de dialogue **Sélectionnez des rôles de serveurs**.  
  
3.  Sélectionnez **Serveur d'applications** dans la liste **Rôles**, puis cliquez sur **Suivant** à deux reprises pour afficher la boîte de dialogue **Sélectionner les services de rôle** pour le rôle Serveur d'applications.  
  
4.  Activez la case à cocher **Serveur Web \(IIS\)**.  Si vous êtes invité à ajouter des fonctionnalités et des services de rôle supplémentaires, cliquez sur **Ajouter les fonctionnalités requises**.  Cliquez sur **Suivant** à deux reprises pour afficher la boîte de dialogue **Sélectionner les services de rôle** pour le rôle Serveur Web \(IIS\).  
  
5.  Développez **Outils de gestion**, puis **Compatibilité avec la gestion IIS 6**.  Sélectionnez **Outils de script IIS 6**.  Si vous êtes invité à ajouter des fonctionnalités et des services de rôle supplémentaires, cliquez sur **Ajouter les services de rôle requis**.  Cliquez sur **Suivant**.  
  
6.  Si l'aperçu des sélections est correct, cliquez sur **Installer**.  
  
7.  Lorsque l'installation est terminée, cliquez sur **Fermer**.  
  
### Pour installer IIS version 7.5 sur Windows 7  
  
1.  Cliquez sur **Démarrer**, puis sur **Panneau de configuration**.  
  
2.  Ouvrez le groupe **Programmes**.  
  
3.  Sous **Programmes et fonctionnalités**, cliquez sur **Activer ou désactiver des fonctionnalités Windows**.  
  
4.  La boîte de dialogue **Contrôle de compte d'utilisateur** s'affiche.  Cliquez sur **Continuer**.  
  
5.  La boîte de dialogue **Fonctionnalités de Windows** s'affiche.  Développez l'élément **Services Internet \(IIS\)**.  
  
6.  Développez l'élément **Services World Wide Web**.  
  
7.  Développez l'élément **Fonctionnalités de développement d'applications**.  
  
8.  Assurez\-vous que les éléments suivants sont sélectionnés :  
  
    1.  **Extensibilité .NET**  
  
    2.  **ASP.NET**  
  
    3.  **Extensions ISAPI**  
  
    4.  **Filtres ISAPI**  
  
9. Sous l'élément **Services World Wide Web**, développez **Fonctionnalités HTTP communes**.  
  
10. Assurez\-vous que l'option **Contenu statique** est sélectionnée.  
  
11. Sous l'élément **Services World Wide Web**, développez **Sécurité**.  
  
12. Assurez\-vous que l'option **Authentification Windows** est sélectionnée.  
  
13. Sous le répertoire **Services Internet \(IIS\)**, développez l'élément **Outils d'administration Web**, puis sélectionnez **Console de gestion IIS**.  
  
14. Développez l'élément **Compatibilité avec la gestion IIS 6**, puis sélectionnez **Outils de script IIS 6**.  
  
15. Sous le répertoire **Services Internet \(IIS\)**, développez l'élément **Microsoft .NET Framework 3.5.1**, puis sélectionnez **Activation HTTP de Windows Communication Foundation**.  
  
16. Cliquez sur **OK**.  
  
### Pour installer IIS version 7.0 sur Windows Server 2008  
  
1.  Dans **Gestionnaire de serveur**, sélectionnez **Rôles**.  Sous **Résumé des rôles**, cliquez sur **Ajouter des rôles**.  
  
2.  Cliquez sur **Suivant** pour afficher la boîte de dialogue **Sélectionnez des rôles de serveurs**.  
  
3.  Sélectionnez **Serveur d'applications** dans la liste **Rôles**, puis cliquez sur **Suivant** à deux reprises pour afficher la boîte de dialogue **Sélectionner les services de rôle** pour le rôle Serveur d'applications.  
  
4.  Activez la case à cocher **Serveur Web \(IIS\)**.  Si vous êtes invité à ajouter des fonctionnalités et des services de rôle supplémentaires, cliquez sur **Ajouter les fonctionnalités requises**.  Cliquez sur **Suivant** à deux reprises pour afficher la boîte de dialogue **Sélectionner les services de rôle** pour le rôle Serveur Web \(IIS\).  
  
5.  Développez **Outils de gestion**, puis **Compatibilité avec la gestion IIS 6**.  Sélectionnez **Outils de script IIS 6**.  Si vous êtes invité à ajouter des fonctionnalités et des services de rôle supplémentaires, cliquez sur **Ajouter les services de rôle requis**.  Cliquez sur **Suivant**.  
  
6.  Si l'aperçu des sélections est correct, cliquez sur **Installer**.  
  
7.  Lorsque l'installation est terminée, cliquez sur **Fermer**.  
  
### Pour installer IIS version 7.0 sur Windows Vista  
  
1.  Cliquez sur Démarrer, puis sur Panneau de configuration.  
  
2.  Sélectionnez le groupe **Programmes**.  
  
3.  Sous **Programmes et fonctionnalités**, cliquez sur **Activer ou désactiver des fonctionnalités Windows**.  
  
4.  La boîte de dialogue **Contrôle de compte d'utilisateur** s'affiche.  Cliquez sur **Continuer**.  
  
5.  La boîte de dialogue **Fonctionnalités de Windows** s'affiche.  Développez l'élément **Services Internet \(IIS\)**.  
  
6.  Développez l'élément **Services World Wide Web**.  
  
7.  Développez l'élément **Fonctionnalités de développement d'applications**.  
  
8.  Assurez\-vous que les éléments suivants sont sélectionnés :  
  
    1.  **Extensibilité .NET**  
  
    2.  **ASP.NET**  
  
    3.  **Extensions ISAPI**  
  
    4.  **Filtres ISAPI**  
  
9. Développez l'élément **Outils d'administration Web**, puis sélectionnez **Console de gestion IIS**.  
  
10. Sous l'élément **Services World Wide Web**, développez **Fonctionnalités HTTP communes**.  
  
11. Assurez\-vous que l'option **Contenu statique** est sélectionnée.  
  
12. Sous l'élément **Services World Wide Web**, développez **Sécurité**.  
  
13. Assurez\-vous que l'option **Authentification Windows** est sélectionnée.  
  
14. Développez l'élément **Compatibilité avec la gestion IIS 6**, puis sélectionnez **Outils de script IIS 6**.  
  
15. Développez l'élément **Microsoft .NET Framework 3.0**, puis sélectionnez **Activation HTTP de Windows Communication Foundation**.  
  
16. Cliquez sur **OK**.  
  
### Pour installer IIS version 6.0 sur Windows Server 2003  
  
1.  Dans **Gérer votre serveur**, cliquez sur **Ajouter ou supprimer un rôle**, puis cliquez sur **Suivant**.  
  
2.  Dans la liste **Rôle du serveur**, sélectionnez **Serveur d'applications \(IIS, ASP.NET\)**, puis cliquez sur **Suivant**.  
  
3.  Activez la case à cocher **Activer ASP.NET**, puis cliquez sur **Suivant**.  
  
4.  Si l'aperçu des sélections est correct, cliquez sur Suivant.  
  
### Pour installer IIS version 5.1 sur Windows XP avec Service Pack 2 et Service Pack 3 installés  
  
1.  Dans le Panneau de configuration, cliquez sur **Ajout\/Suppression de programmes**.  
  
2.  Dans la boîte de dialogue **Ajouter ou supprimer des programmes**, cliquez sur **Ajouter ou supprimer des composants Windows**.  
  
3.  Dans **Assistant Composants de Windows**, activez la case à cocher **Services IIS \(Internet Information Services\)**, puis cliquez sur **Suivant**.  
  
4.  Si la boîte de dialogue **Fichiers nécessaires** s'affiche, insérez le disque d'installation du système d'exploitation, accédez au dossier i386, puis cliquez sur **OK**.  
  
5.  Lorsque l'installation est terminée, cliquez sur **Terminer**.  
  
6.  Fermez la boîte de dialogue **Ajouter ou supprimer des programmes**, puis fermez le **Panneau de configuration**.  
  
### Pour vérifier l'installation d'IIS et d'ASP.NET  
  
1.  Enregistrez le fichier HTML indiqué à la fin de cette rubrique dans le répertoire \\InetPub\\wwwroot racine et nommez\-le Default.aspx.  
  
2.  Ouvrez une nouvelle fenêtre de navigateur.  
  
3.  Tapez `http://localhost/Default.aspx` dans la zone d'adresse et appuyez sur ENTRÉE.  
  
4.  Une page Web contenant le texte « Hello World » doit apparaître.  
  
> [!NOTE]
>  Chaque fois que vous installez une nouvelle version du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], vous devez réinscrire aspnet\_isapi comme extension de service Web pour IIS.  Pour ce faire, émettez la commande `aspnet_regiis –I –enable`.  
  
## Exemple de code  
  
```  
<html>  
   <body>  
       <form >  
           <h3> Hello World  
           </h3>  
       </form>  
   </body>  
</html>  
```