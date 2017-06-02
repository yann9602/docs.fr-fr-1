---
title: "Expressions | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 43a85905-77b5-4893-bb38-1cb9b293d69d
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# Expressions
Cet exemple montre comment utiliser des expressions de base dans un workflow.Il se compose d'un workflow qui calcule des statistiques de salaires de base pour deux employés d'une société fictive.Deux classes, `Employee` et `SalaryStats`, sont définies dans Employee.cs et SalaryStats.cs.Ces classes sont utilisées dans un workflow qui montre comment effectuer des opérations arithmétiques et de chaîne simples sur les propriétés de variables de types complexes.  
  
 Le workflow de calcul des salaires est défini à la fois en XAML et en C\# pour montrer les deux styles de création.La version XAML est contenue dans SalaryCalculation.xaml, et peut être affichée et modifiée dans le concepteur de workflow.La version C\# se trouve dans Program.cs.Les expressions utilisées en XAML sont conformes à la syntaxe Visual Basic et utilisent les activités d'expressions <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> et <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> à exécuter.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] les expressions Visual Basic, consultez [Expressions](http://go.microsoft.com/fwlink/?LinkId=165912)Par ailleurs, les expressions en C\# sont écrites sous la forme d'expressions lambda et utilisent des activités d'expressions <xref:System.Activities.Expressions.LambdaValue%601> et <xref:System.Activities.Expressions.LambdaReference%601>.L'écriture d'expressions sous la forme d'expressions lambda permet au compilateur C\# de fournir une mise en surbrillance de la syntaxe et une vérification statique.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] les expressions lambda en C\#, consultez [Expressions lambda \(Guide de programmation C\#\)](http://go.microsoft.com/fwlink/?LinkId=182082).Si un workflow est créé dans le code à l'aide de Visual Basic, les expressions lambda Visual Basic sont utilisées.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] les expressions lambda en Visual Basic, consultez [Expressions lambda \(Visual Basic\)](http://go.microsoft.com/fwlink/?LinkId=152437).[!INCLUDE[crabout](../../../../includes/crabout-md.md)] la création de workflows à l'aide du code, consultez [Création de workflows, d'activités et d'expressions à l'aide du code impératif](../../../../docs/framework/windows-workflow-foundation//authoring-workflows-activities-and-expressions-using-imperative-code.md).  
  
#### Pour exécuter l'exemple  
  
1.  Ouvrez la solution Expressions.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B ou sélectionnez **Générer la solution** dans le menu **Générer**.  
  
    > [!NOTE]
    >  Pour ouvrir SalaryCalculation.xaml dans le concepteur Visual Studio, vous devez d'abord compiler votre projet pour vérifier que les classes `Employee` et `SalaryStats` sont disponibles pour le concepteur.  
  
3.  Une fois que la génération a réussi, appuyez sur F5 ou sélectionnez **Démarrer le débogage** dans le menu **Déboguer**.Vous pouvez également appuyer sur Ctrl\+F5 ou sélectionner **Exécuter sans débogage** dans le menu **Déboguer** pour effectuer une exécution sans débogage.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Expressions`  
  
## Voir aussi