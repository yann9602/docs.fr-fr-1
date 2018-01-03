---
title: "Utiliser &#39; FilePutObject &#39; au lieu de &#39; FilePut &#39; Lorsque l’argument est de type &#39; objet &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5612c2bd4dc08f767643d2cd865a2ba1a8210c15
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a>Utiliser &#39; FilePutObject &#39; au lieu de &#39; FilePut &#39; Lorsque l’argument est de type &#39; objet &#39;
Le `FilePut` méthode inclut un argument de type `Object`. `FilePutObject` doit être utilisé à la place de `FilePut` pour éviter toute ambiguïté.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Remplacez `FilePut` par `FilePutObject`.  
  
-   Effectuez un cast sur le type de l’argument `Object` pour en faire un type plus spécifique.  
  
-   Utilisez les fonctionnalités disponibles dans l’objet `My.Computer.FileSystem` .  
  
## <a name="see-also"></a>Voir aussi  
   
 [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)  
 [My.Computer.FileSystem.WriteAllBytes](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
