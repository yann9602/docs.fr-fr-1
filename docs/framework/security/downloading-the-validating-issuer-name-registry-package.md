---
title: "T&#233;l&#233;chargement du package de validation du registre des noms d&#39;&#233;metteurs | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
caps.latest.revision: 3
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 3
---
# T&#233;l&#233;chargement du package de validation du registre des noms d&#39;&#233;metteurs
Cette rubrique explique comment télécharger et utiliser le Registre de validation du nom de l'émetteur \(VINR\) dans votre projet.  
  
## Téléchargement du Registre de validation de nom d'émetteur  
 Le VINR est disponible sous forme de package NuGet, qui ajoute les assemblys et les références nécessaires à votre projet.  Si NuGet n'est pas déjà installé, accédez à [nuget.org](http://nuget.org) pour l'installer.  Vous pouvez consulter l'historique de contrôle de version de l'extension en visitant sa page sur NuGet : [Validation Microsoft du registre du nom d'émetteur sur NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)  
  
#### Téléchargement du Registre de validation de nom d'émetteur à l'aide de l'interface utilisateur du gestionnaire de package  
  
1.  Dans Visual Studio, cliquez avec le bouton droit sur votre projet dans l'**Explorateur de solutions**, puis sélectionnez **Gérer les packages NuGet**.  
  
2.  Dans la fenêtre **Gérer les packages NuGet**, cliquez sur la zone de recherche et tapez `ValidatingIssuerNameRegistry`, puis appuyez sur **Entrée**.  
  
3.  Dans le volet de résultats, cliquez sur le bouton **Installer** pour le premier résultat.  
  
4.  Le package démarre le téléchargement.  Avant qu'il soit ajouté à votre projet, le dialogue d'acceptation de licence s'affiche.  Si vous acceptez les termes du contrat de licence, cliquez sur **J'accepte**.  
  
5.  Les derniers assemblys de VINR seront téléchargés et ajoutés à votre projet.  
  
#### Téléchargement du Registre de validation de nom d'émetteur à l'aide de la console de gestionnaire de package  
  
1.  Dans Visual Studio, cliquez sur **Outils**, **Gestionnaire de package de bibliothèques**, puis sur **Console du gestionnaire de package**.  
  
2.  La **Console du gestionnaire de package** apparaît.  Entrez le texte suivant et appuyer sur **Entrée** :  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry  
    ```  
  
3.  Les derniers assemblys de VINR seront téléchargés et ajoutés à votre projet.