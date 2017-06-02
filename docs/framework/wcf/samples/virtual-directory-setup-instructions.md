---
title: "Instructions d&#39;installation du r&#233;pertoire virtuel | Microsoft Docs"
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
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
caps.latest.revision: 36
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 36
---
# Instructions d&#39;installation du r&#233;pertoire virtuel
Les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ont pour but de partager un répertoire virtuel commun nommé servicemodelsamples, mappé au dossier %SystemDrive%\\inetpub\\wwwroot\\servicemodelsamples.  
  
> [!NOTE]
>  %SystemDrive% correspond généralement à C: ou D:, en fonction de l'emplacement de lecteur où Internet Information Services \(IIS\) est installé.  
  
 Vous pouvez exécuter les fichiers Setupvroot.bat et Cleanupvroot.bat à partir des [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) pour créer le répertoire virtuel.Si vous préférez créer le répertoire virtuel manuellement, exécutez les procédures suivantes.  
  
## Procédures  
  
#### Pour créer un répertoire virtuel dans IIS 7.0 ou 7.5  
  
1.  Dans le menu **Démarrer**, cliquez sur **Exécuter**, puis tapez **inetmgr** pour ouvrir le composant logiciel enfichable MMC Internet Information Services \(IIS\).  
  
2.  Dans le volet gauche, développez le nœud portant le nom de l'ordinateur, puis développez le nœud **Sites**.  
  
3.  Cliquez avec le bouton droit sur **Site Web par défaut**, puis sélectionnez **Ajouter une application** pour ouvrir la fenêtre **Ajouter une application**.  
  
4.  Dans cette fenêtre, tapez `servicemodelsamples` en tant qu'alias pour le répertoire virtuel que vous créez.  
  
5.  Créez le répertoire suivant : %SystemDrive%\\inetpub\\wwwroot\\servicemodelsamples  
  
6.  Affectez la valeur %SystemDrive%\\inetpub\\wwwroot\\servicemodelsamples au chemin d'accès physique.La plupart des exemples WCF copient les fichiers exécutables de service dans cet emplacement une fois générés.  
  
7.  Cliquez sur **OK**.L'application Web est créée pour les exemples WCF.  
  
    > [!NOTE]
    >  Cette tâche doit être exécutée une seule fois, car les exemples [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilisent tous la même application Web \(servicemodelsamples\).  
  
    > [!NOTE]
    >  Dans cette documentation, le terme `virtual directory` est synonyme du terme `Web application`.  
  
     Après avoir créé le répertoire virtuel, vous devez définir ses propriétés pour que les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] puissent être exécutés.Pour plus d'informations, consultez ce qui suit.  
  
#### Pour créer un répertoire virtuel dans IIS 5.1 ou 6.0  
  
1.  Ouvrez une fenêtre d'invite de commandes et tapez `start inetmgr` pour ouvrir le composant logiciel enfichable MMC Internet Information Services \(IIS\).  
  
2.  Dans le volet gauche, développez le nœud portant le nom de l'ordinateur, puis développez le nœud **Sites Web**.  
  
3.  Cliquez avec le bouton droit sur **Site Web par défaut** et sélectionnez **Nouveau, Répertoire virtuel** pour ouvrir l'Assistant Création de répertoire virtuel.  
  
4.  Dans l'Assistant, tapez `servicemodelsamples` en tant qu'alias pour le répertoire virtuel que vous créez.  
  
5.  Affectez la valeur %SystemDrive%\\inetpub\\wwwroot\\servicemodelsamples au chemin.La plupart des exemples [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] copient les fichiers exécutables de service dans cet emplacement une fois générés.  
  
6.  Cliquez sur **Suivant**.  
  
7.  Les cases à cocher suivantes sont activées par défaut :  
  
    -   **Lecture**  
  
    -   **Exécuter les scripts \(tels que ASP\)**  
  
8.  Cliquez sur **Suivant**, puis sur **Terminer** pour terminer l'Assistant.  
  
    > [!NOTE]
    >  Cette tâche doit être exécutée une seule fois, car les exemples [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilisent tous le même répertoire virtuel \(servicemodelsamples\).  
  
#### Pour définir des propriétés de répertoire virtuel supplémentaires dans IIS 7.0 ou 7.5  
  
1.  Cliquez sur le nœud servicemodelsamples.Deux vues figurent au bas de la fenêtre.Sélectionnez **Affichage des fonctionnalités** si ce n'est pas encore fait.  
  
2.  Double\-cliquez sur l'entrée affichée pour **Exploration de répertoire**.  
  
3.  Dans le volet Actions, sélectionnez l'option **Activer**.Cela permet d'accéder au répertoire du répertoire à l'aide d'Internet Explorer, ce qui est utile lors du débogage d'un service.  
  
 Enfin, vous devez définir les propriétés de sécurité du dossier servicemodelsamples afin d'autoriser son accès.Pour plus d'informations, consultez ce qui suit.  
  
#### Pour définir des propriétés de répertoire virtuel supplémentaires dans IIS 5.1 ou 6.0  
  
1.  Cliquez avec le bouton droit sur le nœud servicemodelsamples, puis cliquez sur **Propriétés**.  
  
2.  Les cases à cocher suivantes sont activées par défaut :  
  
    -   **Lecture**  
  
    -   **Accès au journal**  
  
    -   **Indexer cette ressource**  
  
3.  Cochez la case **Exploration de répertoire**.Cela permet d'accéder au répertoire du répertoire à l'aide d'Internet Explorer, ce qui est utile lors du débogage d'un service.  
  
#### Pour définir les propriétés de sécurité de ce dossier dans IIS 7.0 ou 7.5  
  
1.  Ouvrez le répertoire %SystemDrive%\\inetpub\\wwwroot\\servicemodelsamples.  
  
2.  Cliquez avec le bouton droit sur le dossier servicemodelsamples et cliquez sur **Partager** ou **Partager avec**.  
  
3.  Cliquez sur la flèche vers le bas à gauche du bouton **Ajouter**.  
  
4.  Sélectionnez l'entrée **Rechercher**.La fenêtre **Sélectionner les utilisateurs ou les groupes** s'ouvre.  
  
5.  Cliquez sur **Avancé**.  
  
6.  Cliquez sur **Emplacements**.La fenêtre **Emplacements** s'ouvre.  
  
7.  Sélectionnez l'entrée correspondant à l'ordinateur en cours d'utilisation.Il est important de sélectionner l'ordinateur local et non une entrée correspondant à tous les domaines ou réseaux répertoriés.Après avoir sélectionné l'ordinateur, cliquez sur **OK**.  
  
8.  Cliquez sur **Rechercher**.Cela permet d'inclure dans les résultats de la recherche les objets associés à l'ordinateur local.  
  
9. Recherchez l'entrée **IIS\_IUSRS** dans la colonne **Nom \(Nom unique relatif\)**.Sélectionnez cette entrée et cliquez sur **OK** pour fermer la fenêtre des résultats de la recherche.  
  
10. Cliquez sur **OK** pour fermer la fenêtre **Sélection d'utilisateurs ou de groupes**.  
  
11. Cliquez sur **Partager** pour enregistrer les modifications.  
  
12. Une fois les modifications de partage apportées, cliquez sur **Terminé** pour fermer la fenêtre **Partage de fichiers**.  
  
#### Pour définir les propriétés de sécurité de ce dossier dans IIS 5.1 ou 6.0  
  
1.  Ouvrez le répertoire %SystemDrive%\\inetpub\\wwwroot\\servicemodelsamples.  
  
2.  Cliquez avec le bouton droit sur le dossier **servicemodelsamples** puis cliquez sur **Partage et sécurité**.  
  
3.  Cliquez sur l'onglet **Sécurité**.  
  
4.  Si vous utilisez IIS 6.0, vérifiez dans la zone **Noms de groupes ou d'utilisateurs** que **Compte Invité Internet** figure dans la liste.  
  
     Si ce n'est pas le cas :  
  
    1.  Cliquez sur **Démarrer**, puis sur **Panneau de configuration**.  
  
    2.  Si l'icône **Comptes d'utilisateurs** n'apparaît pas, cliquez sur **Basculer vers l'affichage des catégories**.  
  
    3.  Cliquez sur l'icône **Comptes d'utilisateurs**.  
  
    4.  Dans « ou une icône du panneau de configuration », cliquez sur **Comptes d'utilisateurs**.  
  
    5.  Dans la boîte de dialogue **Comptes d'utilisateurs**, cliquez sur l'onglet **Avancés**.  
  
    6.  Cliquez sur **Avancé**.  
  
    7.  Dans la boîte de dialogue **Utilisateurs et groupes locaux**, cliquez pour développer le dossier **Utilisateurs**.  
  
    8.  Dans le volet droit, double\-cliquez sur **Compte Invité Internet**.  
  
    9. Dans la boîte de dialogue **Propriétés**, copiez le nom utilisé comme compte Invité Internet.Par défaut, le nom commence par « USR\_ » suivi du nom de l'ordinateur.  
  
    10. Fermez la boîte de dialogue **Propriétés**.  
  
    11. Fermez la boîte de dialogue **Utilisateurs et groupes locaux**.  
  
    12. Fermez la boîte de dialogue **Comptes d'utilisateurs**.  
  
    13. Fermez l'autre boîte de dialogue **Comptes d'utilisateurs**.  
  
    14. Dans la boîte de dialogue **Propriétés de servicemodelsamples**, dans l'onglet **Sécurité**, cliquez sur **Ajouter**.  
  
    15. Tapez le nom de l'ordinateur suivi d'une barre oblique inverse, puis collez le nom du compte d'utilisateur Internet \(myMachineName\\%InternetGuestAccountName%, par exemple\).  
  
    16. Cliquez sur **Vérifier les noms** pour vérifier le nom entré.S'il est valide, ce nom figure en majuscules soulignées.  
  
5.  Pour IIS 6.0, vérifiez également que SERVICE RÉSEAU est répertorié dans la zone **Noms de groupes ou d'utilisateurs**.  
  
     Si SERVICE RÉSEAU n'est pas répertorié :  
  
    1.  Cliquez sur **Ajouter**.  
  
    2.  Dans la boîte de dialogue **Sélectionner les utilisateurs ou les groupes**, tapez le nom de l'ordinateur suivi d'une barre oblique inverse.  
  
    3.  Tapez service après la barre oblique inverse \(sans espace\).  
  
    4.  Cliquez sur **Vérifier les noms**.  
  
    5.  Si plusieurs noms sont trouvés, sélectionnez **SERVICE RÉSEAU** et cliquez sur **OK**.  
  
    6.  Cliquez sur **OK** pour fermer la boîte de dialogue **Sélectionner les utilisateurs ou les groupes**.  
  
6.  Si vous utilisez Windows XP SP2 avec IIS 5.1, vérifiez que Compte Invité Internet et ASPNET sont répertoriés dans la zone **Noms de groupes ou d'utilisateurs**.  
  
     Notez que l'utilisateur ASPNET peut être membre du groupe de sécurité **Utilisateurs** intégré.Dans ce cas, si le groupe **Utilisateurs** est répertorié dans la boîte de dialogue, vous n'avez pas besoin de l'ajouter à la liste des utilisateurs autorisés sous forme d'élément séparé.  
  
     Pour vérifier qu'ASPNET fait partie du groupe de sécurité **Utilisateurs** :  
  
    1.  Dans le menu **Démarrer**, cliquez sur **Panneau de configuration**.  
  
    2.  Cliquez sur l'icône **Comptes d'utilisateurs**.  
  
    3.  Dans la colonne **Groupe**, vérifiez que la valeur affectée à **ASPNET** est « Utilisateurs ».  
  
## Voir aussi  
 [Instructions relatives à l'hébergement dans les Services Internet \(IIS\)](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)