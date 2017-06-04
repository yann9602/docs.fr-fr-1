---
title: "G&#233;n&#233;ration de classes de type de donn&#233;es &#224; partir de XML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# G&#233;n&#233;ration de classes de type de donn&#233;es &#224; partir de XML
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] inclut une nouvelle fonctionnalité pour générer les classes de type de données XML.  Cette rubrique décrit comment générer automatiquement des types de données du flux RSS MSDN Library.  
  
### Obtention du code XML du flux RSS MSDN Library  
  
1.  Dans Internet Explorer, naviguez jusqu'au [flux RSS MSDN](http://go.microsoft.com/fwlink/?LinkId=225209).  
  
2.  Cliquez avec le bouton droit sur la page, puis sélectionnez **Afficher la source**.  
  
3.  Copiez le texte du flux en appuyant sur **Ctrl\+A** pour sélectionner tout le texte, et **Ctrl\+C** pour copier.  
  
### Création des types de données  
  
1.  Ouvrez un fichier de code où le proxy doit être utilisé.  Ce fichier doit faire partie d'un projet [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].  
  
2.  Placez le curseur dans un emplacement du fichier à l'extérieur des classes existantes.  
  
3.  Sélectionnez **Edition**, **Collage spécial**, **Coller du code XML en tant que classes**.  
  
4.  Les classes appelées `rss`, `rssChannel`, `rssChannelImage` et `rssChannelItem` sont créées avec les membres nécessaires pour accéder aux éléments dans le flux RSS.  
  
### Utilisation des classes générées  
  
1.  Une fois les classes générées, elles peuvent être utilisées dans le code comme toute autre classe.  L'exemple suivant retourne une nouvelle instance de la classe `rssChannelImage`.  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
  
    ```