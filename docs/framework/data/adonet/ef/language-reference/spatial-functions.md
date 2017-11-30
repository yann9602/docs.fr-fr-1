---
title: Fonctions spatiales
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 935708457c3ebc8257b2495da36886468be1c706
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="spatial-functions"></a>Fonctions spatiales
Il n'existe aucun format littéral pour les types spatiaux. Toutefois, vous pouvez utiliser des fonctions canoniques Entity Framework que vous appelez à l'aide de chaînes au format texte connu. Par exemple, l'appel de fonction suivant crée un point géométrique :  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 Le [spatialedmfunctions, méthodes](http://msdn.microsoft.com/library/hh749531.aspx) page répertorie toutes les méthodes canoniques spatiales Entity Framework. Cliquez sur une méthode qui vous intéresse pour afficher les paramètres qui doivent être passés à une fonction.
