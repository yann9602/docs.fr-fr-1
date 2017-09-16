---
title: "Téléchargement du package de Registre des noms d'émetteurs de validation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
caps.latest.revision: 3
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d7aa4e4010da70f90bb18db9cd4e8179925bb58d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="downloading-the-validating-issuer-name-registry-package"></a>Téléchargement du package de Registre des noms d'émetteurs de validation
Cette rubrique explique comment télécharger et utiliser le Registre des noms d’émetteurs de validation (VINR, Validating Issuer Name Registry) dans votre projet.  
  
## <a name="downloading-the-validating-issuer-name-registry"></a>Téléchargement du Registre des noms d’émetteurs de validation  
 Le Registre VINR est disponible sous forme de package NuGet, qui ajoute les assemblys et les références nécessaires à votre projet. Si vous n’avez pas encore installé NuGet, accédez à [nuget.org](http://nuget.org) pour l’installer. Vous pouvez voir l’historique de gestion de version de l’extension en accédant à sa page sur NuGet : [Registre des noms d’émetteurs de validation Microsoft sur NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)  
  
#### <a name="downloading-the-validating-issuer-name-registry-by-using-the-package-manager-gui"></a>Téléchargement du Registre des noms d’émetteurs de validation à l’aide de l’interface graphique utilisateur du Gestionnaire de package  
  
1.  Dans Visual Studio, cliquez sur votre projet dans l’**Explorateur de solutions**, puis sélectionnez **Gérer les packages NuGet**.  
  
2.  Dans la fenêtre **Gérer les packages NuGet**, cliquez sur la zone de recherche et tapez `ValidatingIssuerNameRegistry`, puis appuyez sur **Entrée**.  
  
3.  Dans le volet de résultats, cliquez sur le bouton **Installer** pour le premier résultat.  
  
4.  Le téléchargement du package commence. Avant l’ajout du package à votre projet, la boîte de dialogue d’acceptation de licence s’affiche. Si vous êtes d’accord avec les termes du contrat de licence, cliquez sur **Accepter**.  
  
5.  Les assemblys VINR les plus récents seront téléchargés et ajoutés à votre projet.  
  
#### <a name="downloading-the-validating-issuer-name-registry-by-using-the-package-manager-console"></a>Téléchargement du Registre des noms d’émetteurs de validation à l’aide de la console du Gestionnaire de package  
  
1.  Dans Visual Studio, cliquez sur **Outils**, **Gestionnaire de package de bibliothèque**, puis **Console du Gestionnaire de package**.  
  
2.  La **Console du Gestionnaire de package** s’affiche. Tapez le texte suivant et appuyez sur **Entrée** :  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry  
    ```  
  
3.  Les assemblys VINR les plus récents seront téléchargés et ajoutés à votre projet.

