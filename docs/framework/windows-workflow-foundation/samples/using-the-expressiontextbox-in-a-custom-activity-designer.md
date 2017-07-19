---
title: "Utilisation d&#39;ExpressionTextBox dans un concepteur d&#39;activit&#233;s personnalis&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Utilisation d&#39;ExpressionTextBox dans un concepteur d&#39;activit&#233;s personnalis&#233;es
Cet exemple montre comment utiliser le <xref:System.Activities.Presentation.View.ExpressionTextBox> dans un concepteur d'activités personnalisées.L'activité personnalisée, `MultiAssign`, assigne deux valeurs de chaîne à deux variables String.Certains contrôles <xref:System.Activities.Presentation.View.ExpressionTextBox> sont liés à <xref:System.Activities.InArgument>s et d'autres à <xref:System.Activities.OutArgument>s.  
  
## Détails de l'exemple  
 Le `ArgumentToExpressionConverter` est le convertisseur de type utilisé lors de la liaison d'expressions aux arguments.Affectez `In` ou `Out` à `ConverterParameter`.`InOut` n'est pas pris en charge.  
  
 L'attribut `UseLocationExpression` est utilisé sur `OutArgument`s pour spécifier que l'expression doit être une expression L\-value \(« left value » ou « location value »\).Dans la plupart des cas, une expression L\-value est un identificateur Visual Basic valide utilisé pour indiquer que le `OutArgument` qui est retourné est un nom de variable ou d'argument.  
  
 L'attribut `MaxLines` a la valeur un dans cet exemple et `MinLines` n'est pas défini.Cela indique que le <xref:System.Activities.Presentation.View.ExpressionTextBox> a une taille fixe d'une ligne indépendamment de la quantité de texte tapée par l'utilisateur.Pour permettre au <xref:System.Activities.Presentation.View.ExpressionTextBox> de s'agrandir pour s'ajuster à l'entrée d'utilisateur, affectez à `MaxLines` une valeur supérieure à `MinLines`.  
  
 Un ExpressionTextBox peut être lié uniquement aux arguments et ne peut pas être lié aux propriétés CLR.  
  
#### Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier ExpressionTextBoxSample.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B.  
  
#### Pour exécuter cet exemple  
  
1.  Ajoutez une nouvelle application console de workflow à la solution.  
  
2.  Ajoutez une référence au projet **ExpressionTextBoxSample** à partir du nouveau projet Application console de workflow.  
  
3.  Générez la solution.  
  
4.  Faites glisser l'activité **MultiAssign** à partir de la boîte à outils et déposez\-la dans le workflow.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## Voir aussi  
 <xref:System.Activities.Presentation.View.ExpressionTextBox>   
 [Développement d'applications avec Workflow Designer](../Topic/Developing%20Applications%20with%20the%20Workflow%20Designer.md)