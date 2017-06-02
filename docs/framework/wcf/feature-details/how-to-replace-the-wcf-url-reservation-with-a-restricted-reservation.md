---
title: "Proc&#233;dure&#160;: remplacer la r&#233;servation d&#39;URL&#160;WCF par une r&#233;servation restreinte | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2754d223-79fc-4e2b-a6ce-989889f2abfa
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Proc&#233;dure&#160;: remplacer la r&#233;servation d&#39;URL&#160;WCF par une r&#233;servation restreinte
Une réservation d'URL vous permet de limiter les personnes qui reçoivent les messages d'une URL ou d'un jeu d'URL.Une réservation se compose d'un modèle d'URL, d'une liste de contrôle d'accès \(ACL\) et d'un jeu d'indicateurs.Le modèle d'URL définit les URL affectées par la réservation.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] le traitement des modèles d'URL, consultez [Routage des demandes entrantes](http://go.microsoft.com/fwlink/?LinkId=136764).L'ACL contrôle quel utilisateur ou groupe d'utilisateurs est autorisé à recevoir des messages en provenance des URL spécifiées.Les indicateurs spécifient si la réservation consiste à donner directement à un utilisateur ou à un groupe l'autorisation d'écouter l'URL ou à déléguer l'autorisation d'écouter à d'autres processus.  
  
 Dans le cadre de la configuration du système d'exploitation par défaut, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] crée une réservation accessible globalement pour le port 80, afin de permettre à tous les utilisateurs d'exécuter des applications qui utilisent une double liaison HTTP pour la communication en duplex.Étant donné que l'ACL sur cette réservation concerne tous les utilisateurs, les administrateurs ne peuvent pas explicitement accorder ou refuser l'autorisation d'écouter une URL ou un jeu d'URL.Cette rubrique explique comment supprimer cette réservation et comment la recréer avec une ACL restreinte.  
  
 Sur [!INCLUDE[wv](../../../../includes/wv-md.md)] ou [!INCLUDE[lserver](../../../../includes/lserver-md.md)], vous pouvez consulter toutes les réservations d'URL HTTP d'une invite de commandes de niveau élevé en tapant `netsh http show urlacl`.L'exemple suivant montre ce à quoi une réservation d'URL [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] doit ressembler.  
  
```  
Reserved URL : http://+:80/Temporary_Listen_Addresses/  
        User: \Everyone  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;WD)  
```  
  
 La réservation se compose d'un modèle d'URL utilisé lorsqu'une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise une double liaison HTTP pour la communication en duplex.Les URL de cette forme sont utilisées pour qu'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] renvoie des messages au client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] lors de la communication sur une double liaison HTTP.Tous les utilisateurs sont autorisés à écouter l'URL, mais pas à déléguer l'écoute à un autre processus.Enfin, l'ACL est décrite en langage SDDL \(Security Descriptor Definition Language\).[!INCLUDE[crabout](../../../../includes/crabout-md.md)] SDDL, consultez [SDDL](http://go.microsoft.com/fwlink/?LinkId=136789).  
  
### Pour supprimer la réservation d'URL WCF  
  
1.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, cliquez sur **Accessoires**, cliquez avec le bouton droit sur **Invite de commandes**, puis cliquez sur **Exécuter en tant qu'administrateur** dans le menu contextuel qui s'affiche.Cliquez sur **Continuer** dans la fenêtre Contrôle de compte d'utilisateur \(UAC\) qui peut demander des autorisations pour continuer.  
  
2.  Dans la fenêtre d'invite de commandes, tapez **netsh http delete urlacl url\=http:\/\/\+:80\/Temporary\_Listen\_Addresses\/**.  
  
3.  Si la réservation est supprimée avec succès, le message suivant s'affiche.**URL reservation successfully deleted**  
  
## Création d'un nouveau groupe de sécurité et d'une nouvelle réservation d'URL restreinte  
 Pour remplacer la réservation d'URL [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] par une réservation restreinte, vous devez d'abord créer un groupe de sécurité.Pour ce faire, deux méthodes s'offrent à vous : à partir d'une invite de commandes ou de la console de gestion de l'ordinateur.L'utilisation d'une seule de ces méthodes suffit.  
  
#### Pour créer un groupe de sécurité à partir d'une invite de commandes  
  
1.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, cliquez sur **Accessoires**, cliquez avec le bouton droit sur **Invite de commandes**, puis cliquez sur **Exécuter en tant qu'administrateur** dans le menu contextuel qui s'affiche.Cliquez sur **Continuer** dans la fenêtre Contrôle de compte d'utilisateur \(UAC\) qui peut demander des autorisations pour continuer.  
  
2.  À l'invite de commandes, tapez **net localgroup "\<security group name\>" \/comment:"\<security group description\>" \/add**.Remplacez **\<security group name\>** par le nom du groupe de sécurité que vous souhaitez créer et **\<security group description\>** par une description appropriée du groupe de sécurité en question.  
  
3.  Si le groupe de sécurité est créé avec succès, le message suivant s'affiche.**The command completed successfully.**  
  
#### Pour créer un groupe de sécurité à partir de la console de gestion de l'ordinateur  
  
1.  Cliquez successivement sur **Démarrer**, **Panneau de configuration**, **Outils d'administration** et sur **Gestion de l'ordinateur** pour ouvrir la console de gestion de l'ordinateur.Cliquez sur **Continuer** dans la fenêtre Contrôle de compte d'utilisateur \(UAC\) qui peut demander des autorisations pour continuer.  
  
2.  Cliquez successivement sur **Outils système** et sur **Utilisateurs et groupes locaux**, cliquez avec le bouton droit sur le dossier **Groupes**, puis cliquez sur **Nouveau groupe** dans le menu contextuel qui s'affiche.Tapez les **Nom du groupe** et **Description** souhaités, ainsi que d'autres informations de ce nouveau groupe de sécurité, puis cliquez sur le bouton **Créer** pour créer le groupe de sécurité.  
  
#### Pour créer la réservation d'URL restreinte  
  
1.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, cliquez sur **Accessoires**, cliquez avec le bouton droit sur **Invite de commandes**, puis cliquez sur **Exécuter en tant qu'administrateur** dans le menu contextuel qui s'affiche.Cliquez sur **Continuer** dans la fenêtre Contrôle de compte d'utilisateur \(UAC\) qui peut demander des autorisations pour continuer.  
  
2.  À l'invite de commandes, tapez **netsh http add urlacl url\=http:\/\/\+:80\/Temporary\_Listen\_Addresses\/ user\="\<machine name\>\\\<security group name\>**.Remplacez **\<machine name\>** par le nom de l'ordinateur sur lequel le groupe doit être créé et **\<security group name\>** par le nom du groupe de sécurité que vous avez précédemment créé.  
  
3.  Si la réservation est créée avec succès, le message suivant s'affiche.**URL reservation successfully added**.