---
title: "Fonctions spatiales | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Fonctions spatiales
Il n'existe aucun format littéral pour les types spatiaux.  Toutefois, vous pouvez utiliser des fonctions canoniques Entity Framework que vous appelez à l'aide de chaînes au format texte connu.  Par exemple, l'appel de fonction suivant crée un point géométrique :  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 La page [SpatialEdmFunctions, méthodes](http://msdn.microsoft.com/library/hh749531.aspx) répertorie toutes les méthodes canoniques spatiales Entity Framework.  Cliquez sur une méthode qui vous intéresse pour afficher les paramètres qui doivent être passés à une fonction.