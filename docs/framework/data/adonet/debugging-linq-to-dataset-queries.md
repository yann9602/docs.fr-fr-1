---
title: "D&#233;bogage des requ&#234;tes LINQ to DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f4c54015-8ce2-4c5c-8d18-7038144cc66d
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# D&#233;bogage des requ&#234;tes LINQ to DataSet
[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] prend en charge le débogage du code  [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].  Il existe cependant certaines différences entre le débogage de code managé [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] et non\-[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. La plupart des fonctionnalités de débogage sont compatibles avec les instructions [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], notamment l'exécution pas à pas, la définition de points d'arrêt et la consultation de résultats dans les fenêtres du débogueur.  Cependant, l'exécution différée des requêtes a des effets secondaires qui doivent être pris en compte lors du débogage du code [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], de même qu'il existe certaines limitations d'utilisation de Modifier &amp; Continuer.  Cette rubrique traite des aspects du débogage qui sont spécifiques à [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] par rapport au code managé non\-[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].  
  
## Affichage des résultats  
 Vous pouvez consulter le résultat d'une instruction [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] à l'aide des DataTips, de la fenêtre Espion et de la boîte de dialogue Espion express.  En utilisant une fenêtre source, vous pouvez suspendre le pointeur sur une requête dans la fenêtre source pour afficher un DataTip.  Vous pouvez copier une variable [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] et la coller dans la fenêtre Espion ou dans la boîte de dialogue Espion express. Dans [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], une requête n'est pas évaluée lorsqu'elle est créée ou déclarée, mais uniquement lors de son exécution.  On parle alors d'*exécution différée*.  Par conséquent, la variable de requête ne possède de valeur que lorsqu'elle est évaluée.  Pour plus d'informations, consultez [Requêtes dans LINQ to DataSet](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md).  
  
 Pour afficher les résultats d'une requête, le débogueur doit l'évaluer.  Cette évaluation implicite se produit lorsque vous consultez le résultat d'une requête [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dans le débogueur, et elle entraîne quelques effets dont vous devez tenir compte.  Chaque évaluation de la requête prend du temps.  Le développement du nœud de résultats est long.  Ainsi, pour certaines requêtes, une évaluation répétée peut diminuer considérablement les performances.  L'évaluation d'une requête provoque aussi des effets secondaires, à savoir des modifications de la valeur des données ou de l'état du programme.  Toutefois, les requêtes ne présentent pas toutes des effets secondaires.  Pour savoir si une requête peut être évaluée sans risque et sans effets secondaires, vous devez comprendre le code qui implémente la requête.  Pour plus d'informations, consultez [Effets secondaires et expressions](../Topic/Side%20Effects%20and%20Expressions.md).  
  
## Modifier & Continuer  
 Modifier & Continuer ne prend pas en charge les modifications apportées aux requêtes [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].  Si vous ajoutez, supprimez ou modifiez une instruction [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] pendant une session de débogage, une boîte de dialogue s'affiche pour signaler que la modification n'est pas prise en charge par Modifier &amp; Continuer.  À ce stade, vous pouvez annuler les modifications apportées ou arrêter la session de débogage et redémarrer une nouvelle session avec le code modifié.  
  
 De plus, Modifier & Continuer ne prend pas en charge la modification du type ou de la valeur d'une variable utilisée dans une instruction [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].  Ici aussi, vous pouvez annuler les modifications apportées ou arrêter et redémarrer la session de débogage.  
  
 Dans Visual C\# de Visual Studio, vous ne pouvez pas utiliser Modifier & Continuer dans un code d'une méthode contenant une requête [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].  
  
 Dans Visual Basic de Visual Studio, vous pouvez utiliser Modifier & Continuer dans un code non\-[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], même dans une méthode contenant une requête [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].  Vous pouvez ajouter ou supprimer du code avant l'instruction [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], même si les modifications apportées concernent le numéro de ligne de la requête [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].  Votre expérience de débogage Visual Basic pour du code non\-[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] reste telle qu'elle était avant l'introduction de [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].  Toutefois, vous ne pouvez pas modifier, ajouter ou supprimer une requête [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], sauf si vous souhaitez arrêter le débogage afin d'appliquer les modifications apportées.  
  
## Voir aussi  
 [Débogage du code managé](../Topic/Debugging%20Managed%20Code.md)   
 [Guide de programmation](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)