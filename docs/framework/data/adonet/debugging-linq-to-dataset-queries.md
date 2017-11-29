---
title: "Débogage des requêtes LINQ to DataSet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4c54015-8ce2-4c5c-8d18-7038144cc66d
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 964a4d051600621d581e05dcf6b518b2766e2750
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="debugging-linq-to-dataset-queries"></a>Débogage des requêtes LINQ to DataSet
[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] prend en charge le débogage du code  [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Il y a cependant certaines différences entre le débogage de code managé [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] et non-[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. La plupart des fonctionnalités de débogage sont compatibles avec les instructions [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], notamment l'exécution pas à pas, la définition de points d'arrêt et la consultation des résultats dans les fenêtres du débogueur. Toutefois, différée l’exécution dans a des effets dont vous devez tenir compte lors du débogage de requête [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] de code et il existe quelques limitations à l’utilisation de modifier & Continuer. Cette rubrique traite des aspects du débogage qui sont uniques à [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] par rapport à non -[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] du code managé.  
  
## <a name="viewing-results"></a>Affichage des résultats  
 Vous pouvez consulter le résultat d’une [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] instruction à l’aide des DataTips, de la fenêtre Espion et de la boîte de dialogue Espion express. En utilisant une fenêtre source, vous pouvez suspendre le pointeur sur une requête dans la fenêtre source pour afficher un DataTip. Vous pouvez copier une variable [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] et la coller dans la fenêtre Espion ou dans la boîte de dialogue Espion express. Dans [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], une requête n'est pas évaluée lorsqu'elle est créée ou déclarée, mais uniquement lors de son exécution. Il s’agit *exécution différée*. Par conséquent, la variable de requête ne possède de valeur que lorsqu'elle est évaluée. Pour plus d’informations, consultez [requêtes dans LINQ to DataSet](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md).  
  
 Pour afficher les résultats d'une requête, le débogueur doit l'évaluer. Cette évaluation implicite se produit lorsque vous affichez un [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] résultat de la requête dans le débogueur et elle entraîne quelques effets dont vous devez prendre en compte. Chaque évaluation de la requête prend du temps. Le développement du nœud de résultats est long. Ainsi, pour certaines requêtes, une évaluation répétée peut diminuer considérablement les performances. L'évaluation d'une requête provoque aussi des effets secondaires, à savoir des modifications de la valeur des données ou de l'état du programme. Toutefois, les requêtes ne présentent pas toutes des effets secondaires. Pour savoir si une requête peut être évaluée sans risque et sans effets secondaires, vous devez comprendre le code qui implémente la requête. Pour plus d’informations, consultez [effets secondaires et Expressions](http://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e).  
  
## <a name="edit-and-continue"></a>Modifier & Continuer  
 Modifier & Continuer ne prend pas en charge les modifications apportées aux [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] des requêtes. Si vous ajouter, supprimer ou modifier un [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] instruction pendant une session de débogage, une boîte de dialogue s’affiche indiquant que la modification n’est pas pris en charge par Modifier & Continuer. À ce stade, vous pouvez annuler les modifications apportées ou arrêter la session de débogage et redémarrer une nouvelle session avec le code modifié.  
  
 De plus, Modifier & Continuer ne prend pas en charge la modification du type ou la valeur d’une variable qui est utilisée dans un [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] instruction. Ici aussi, vous pouvez annuler les modifications apportées ou arrêter et redémarrer la session de débogage.  
  
 Dans Visual c# dans Visual Studio, vous ne pouvez pas utiliser Modifier & Continuer dans un code d’une méthode qui contient un [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] requête.  
  
 En Visual Basic dans Visual Studio, vous pouvez utiliser Modifier & Continuer non-[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] code, même dans une méthode qui contient un [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] requête. Vous pouvez ajouter ou supprimer du code avant la [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] instruction, même si les modifications affectent le numéro de ligne de la [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] requête. Votre expérience de débogage Visual Basic non -[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] code reste le même qu’elle était avant [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] a été introduit. Vous ne pouvez pas modifier, ajouter ou supprimer un [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] de requête, toutefois, sauf si vous arrêtez le débogage afin d’appliquer les modifications.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage du code managé](/visualstudio/debugger/debugging-managed-code)  
 [Guide de programmation](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
