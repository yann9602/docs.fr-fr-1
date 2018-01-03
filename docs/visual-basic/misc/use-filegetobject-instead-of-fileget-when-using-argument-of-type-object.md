---
title: "Utiliser &#39; FileGetObject &#39; au lieu de &#39; FileGet &#39; Lorsque l’argument est de type &#39; objet &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 090b8088-895a-482a-9362-606596bac304
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c5be466a8a0339bdb57818755d85a26d632d774
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a>Utiliser &#39; FileGetObject &#39; au lieu de &#39; FileGet &#39; Lorsque l’argument est de type &#39; objet &#39;
La méthode `FileGet` comprend un argument de type `Object`. `FileGetObject` doit être utilisé à la place de `FileGet` pour éviter toute ambiguïté.  
  
 Notez que les fonctionnalités offertes par `My.Computer.Filesystem` proposent une plus grande facilité d’utilisation et des performances accrues par rapport à `FileGet` ou `FileGetObject`.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Remplacez `FileGet` par `FileGetObject`.  
  
2.  Effectuez un cast sur le type de l’argument `Object` pour en faire un type plus spécifique.  
  
## <a name="see-also"></a>Voir aussi  
   
 [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
