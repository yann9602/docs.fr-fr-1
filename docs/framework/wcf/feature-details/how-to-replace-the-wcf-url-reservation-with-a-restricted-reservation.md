---
title: "Procédure : remplacer la réservation d'URL WCF par une réservation restreinte"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2754d223-79fc-4e2b-a6ce-989889f2abfa
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8c25403f298444732f6787979add595bd877bb2c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation"></a>Procédure : remplacer la réservation d'URL WCF par une réservation restreinte
Une réservation d'URL vous permet de limiter les personnes qui reçoivent les messages d'une URL ou d'un jeu d'URL. Une réservation se compose d'un modèle d'URL, d'une liste de contrôle d'accès (ACL) et d'un jeu d'indicateurs. Le modèle d'URL définit les URL affectées par la réservation. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]mode de traitement des modèles d’URL, consultez [le routage des demandes entrantes](http://go.microsoft.com/fwlink/?LinkId=136764). L'ACL contrôle quel utilisateur ou groupe d'utilisateurs est autorisé à recevoir des messages en provenance des URL spécifiées. Les indicateurs spécifient si la réservation consiste à donner directement à un utilisateur ou à un groupe l'autorisation d'écouter l'URL ou à déléguer l'autorisation d'écouter à d'autres processus.  
  
 Dans le cadre de la configuration du système d'exploitation par défaut, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] crée une réservation accessible globalement pour le port 80, afin de permettre à tous les utilisateurs d'exécuter des applications qui utilisent une double liaison HTTP pour la communication en duplex. Étant donné que l'ACL sur cette réservation concerne tous les utilisateurs, les administrateurs ne peuvent pas explicitement accorder ou refuser l'autorisation d'écouter une URL ou un jeu d'URL. Cette rubrique explique comment supprimer cette réservation et comment la recréer avec une ACL restreinte.  
  
 Sur [!INCLUDE[wv](../../../../includes/wv-md.md)] ou [!INCLUDE[lserver](../../../../includes/lserver-md.md)], vous pouvez consulter toutes les réservations d'URL HTTP d'une invite de commandes de niveau élevé en tapant `netsh http show urlacl`.  L'exemple suivant montre ce à quoi une réservation d'URL [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] doit ressembler.  
  
```  
Reserved URL : http://+:80/Temporary_Listen_Addresses/  
        User: \Everyone  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;WD)  
```  
  
 La réservation se compose d'un modèle d'URL utilisé lorsqu'une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise une double liaison HTTP pour la communication en duplex. Les URL de cette forme sont utilisées pour qu'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] renvoie des messages au client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] lors de la communication sur une double liaison HTTP. Tous les utilisateurs sont autorisés à écouter l'URL, mais pas à déléguer l'écoute à un autre processus. Enfin, l'ACL est décrite en langage SDDL (Security Descriptor Definition Language). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]SSDL, consultez [SSDL](http://go.microsoft.com/fwlink/?LinkId=136789)  
  
### <a name="to-delete-the-wcf-url-reservation"></a>Pour supprimer la réservation d'URL WCF  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur **Accessoires**, avec le bouton droit **invite de commandes** et cliquez sur **d’identification Administrateur** dans le menu contextuel qui s’affiche. Cliquez sur **continuer** dans la fenêtre de contrôle de compte d’utilisateur (UAC) qui peut demander des autorisations pour continuer.  
  
2.  Tapez dans **netsh http delete urlacl url = http : / / + :80/Temporary_Listen_Addresses/** dans la fenêtre d’invite de commandes.  
  
3.  Si la réservation est supprimée avec succès, le message suivant s'affiche. **Réservation d’URL a été supprimée**  
  
## <a name="creating-a-new-security-group-and-new-restricted-url-reservation"></a>Création d'un nouveau groupe de sécurité et d'une nouvelle réservation d'URL restreinte  
 Pour remplacer la réservation d'URL [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] par une réservation restreinte, vous devez d'abord créer un groupe de sécurité. Pour ce faire, deux méthodes s'offrent à vous : à partir d'une invite de commandes ou de la console de gestion de l'ordinateur. L'utilisation d'une seule de ces méthodes suffit.  
  
#### <a name="to-create-a-new-security-group-from-a-command-prompt"></a>Pour créer un groupe de sécurité à partir d'une invite de commandes  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur **Accessoires**, avec le bouton droit **invite de commandes** et cliquez sur **d’identification Administrateur** dans le menu contextuel qui s’affiche. Cliquez sur **continuer** dans la fenêtre de contrôle de compte d’utilisateur (UAC) qui peut demander des autorisations pour continuer.  
  
2.  Tapez dans **net localgroup «\<nom de groupe de sécurité > « / commentaire : «\<description du groupe de sécurité > » / ajouter** à l’invite de commandes. En remplaçant  **\<nom de groupe de sécurité >** avec le nom du groupe de sécurité que vous souhaitez créer et  **\<description du groupe de sécurité >** avec une description appropriée pour le groupe de sécurité.  
  
3.  Si le groupe de sécurité est créé avec succès, le message suivant s'affiche. **La commande s’est terminée correctement.**  
  
#### <a name="to-create-a-new-security-group-from-the-computer-management-console"></a>Pour créer un groupe de sécurité à partir de la console de gestion de l'ordinateur  
  
1.  Cliquez sur **Démarrer**, cliquez sur **le panneau de configuration**, cliquez sur **outils d’administration**, puis cliquez sur **gestion de l’ordinateur** pour ouvrir l’ordinateur Console de gestion. Cliquez sur **continuer** dans la fenêtre de contrôle de compte d’utilisateur (UAC) qui peut demander des autorisations pour continuer.  
  
2.  Cliquez sur **Outils système**, cliquez sur **utilisateurs et groupes locaux**, avec le bouton droit **groupes** dossier puis cliquez sur **nouveau groupe** dans le menu contextuel qui s’affiche. Type dans l’élément **nom de groupe**, **Description** et d’autres détails de ce nouveau groupe de sécurité cliquez sur le **créer** bouton permettant de créer le groupe de sécurité.  
  
#### <a name="to-create-the-restricted-url-reservation"></a>Pour créer la réservation d'URL restreinte  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur **Accessoires**, avec le bouton droit **invite de commandes** et cliquez sur **d’identification Administrateur** dans le menu contextuel qui s’affiche. Cliquez sur **continuer** dans la fenêtre de contrôle de compte d’utilisateur (UAC) qui peut demander des autorisations pour continuer.  
  
2.  Tapez dans **netsh http ajouter urlacl url = http : / / + : 80/Temporary_Listen_Addresses/utilisateur = «\<nom de l’ordinateur >\\< nom de groupe de sécurité\>**  à l’invite de commandes. En remplaçant  **\<nom de l’ordinateur >** avec le nom de l’ordinateur sur lequel le groupe doit être créé et  **\<nom de groupe de sécurité >** avec le nom du groupe de sécurité que vous avez créé précédemment.  
  
3.  Si la réservation est créée avec succès, le message suivant s'affiche. **Réservation d’URL ajoutée avec succès**.
