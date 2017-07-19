---
title: "Exceptions d&#39;h&#233;bergement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Exceptions d&#39;h&#233;bergement
Cette rubrique répertorie toutes les exceptions générées par l'hébergement.  
  
## Liste des exceptions  
  
|Code de la ressource|Chaîne de la ressource|  
|--------------------------|----------------------------|  
|Hosting\_AddressIsAbsoluteUri|L'URI complet n'est pas autorisé.Les URI complets ne sont pas pris en compte pour l'API ServiceHostingEnvironment.EnsureServiceAvailable.Utilisez un chemin d'accès virtuel pour le service correspondant.|  
|Hosting\_BuildProviderCouldNotCreateType|Le type CLR spécifié ne peut pas être chargé pendant la compilation de service.Vérifiez que ce type est défini dans un fichier source situé dans le répertoire \\\\App\_Code de l'application, contenu dans un assembly compilé situé dans le répertoire \\\\bin de l'application ou présent dans un assembly installé dans le Global Assembly Cache.Le nom du type respecte la casse.Les répertoires, tels que \\\\App\_Code et \\\\bin, doivent se situer dans le répertoire racine de l'application.Les répertoires \\\\App\_Code et \\\\bin ne peuvent pas être imbriqués dans des sous\-répertoires.|