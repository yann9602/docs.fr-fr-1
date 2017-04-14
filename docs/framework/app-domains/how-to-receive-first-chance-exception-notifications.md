---
title: "Comment&#160;: recevoir des notifications des exceptions de premi&#232;re chance | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "exceptions, notifications de première chance"
  - "notifications d'exceptions de première chance"
ms.assetid: 66f002b8-a97d-4a6e-a503-2cec01689113
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: recevoir des notifications des exceptions de premi&#232;re chance
L'événement <xref:System.AppDomain.FirstChanceException> de la classe <xref:System.AppDomain> vous permet de recevoir la notification qu'une exception a été levée, avant que le Common Language Runtime n'ait commencé à rechercher des gestionnaires d'exceptions.  
  
 L'événement est déclenché au niveau du domaine d'application.  Un thread d'exécution peut traverser plusieurs domaines d'application, donc une exception qui n'est pas gérée dans un domaine d'application pourrait être contrôlée dans un autre domaine d'application.  La notification se produit dans chaque domaine d'application qui a ajouté un gestionnaire pour l'événement, jusqu'à ce qu'un domaine d'application gère l'exception.  
  
 Les procédures et exemples dans cet article indiquent comment recevoir des notifications des exceptions de première chance dans un programme simple qui a un domaine d'application, et dans un domaine d'application que vous créez.  
  
 Pour obtenir un exemple plus complexe qui couvre plusieurs domaines d'application, consultez l'exemple pour l'événement <xref:System.AppDomain.FirstChanceException>.  
  
## Réception de notifications des exceptions de première chance dans le domaine d'application par défaut  
 Dans la procédure suivante, le point d'entrée de l'application \(la méthode `Main()`\) est exécutée dans le domaine d'application par défaut.  
  
#### Pour illustrer des notifications des exceptions de première chance dans le domaine d'application par défaut  
  
1.  Définissez un gestionnaire d'événements pour l'événement <xref:System.AppDomain.FirstChanceException>, à l'aide d'une fonction lambda et attachez\-le à l'événement.  Dans cet exemple, le gestionnaire d'événements imprime le nom du domaine d'application dans lequel l'événement a été géré ainsi que la propriété <xref:System.Exception.Message%2A> de l'exception.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#2)]  
  
2.  Levez une exception et interceptez\-la.  Avant que l'exécution ne trouve le gestionnaire d'exceptions, l'événement <xref:System.AppDomain.FirstChanceException> est déclenché et affiche un message.  Ce message est suivi par le message affiché par le gestionnaire d'exceptions.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#3)]  
  
3.  Levez une exception mais ne l'interceptez pas.  Avant que le runtime ne recherche le gestionnaire d'exceptions, l'événement <xref:System.AppDomain.FirstChanceException> est déclenché et affiche un message.  Il n'y a aucun gestionnaire d'exceptions, donc l'application s'arrête.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#4)]  
  
     Le code affiché dans les trois premières étapes de cette procédure forme une application console complète.  La sortie de l'application varie en fonction du nom du fichier .exe car le nom du domaine d'application par défaut se compose du nom et de l'extension du fichier .exe.  Consultez l'exemple de sortie suivant.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#5)]  
  
## Réception de notifications des exceptions de première chance dans un autre domaine d'application  
 Si votre programme contient plusieurs domaines d'application, vous pouvez choisir les domaines d'application qui reçoivent des notifications.  
  
#### Pour recevoir des notifications des exceptions de première chance dans un domaine d'application que vous créez  
  
1.  Définissez un gestionnaire d'événements pour l'événement <xref:System.AppDomain.FirstChanceException>.  Cet exemple utilise une méthode `static` \(méthode`Shared` en Visual Basic\) qui imprime le nom du domaine d'application où l'événement a été contrôlé ainsi que la propriété <xref:System.Exception.Message%2A> de l'exception.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#3)]  
  
2.  Créez un domaine d'application et ajoutez le gestionnaire d'événements à l'événement <xref:System.AppDomain.FirstChanceException> pour ce domaine d'application.  Dans cet exemple, le domaine d'application est nommé `AD1`.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#2)]  
  
     Vous pouvez gérer de la même façon cet événement dans le domaine d'application par défaut.  Utilisez le `static` \(`Shared` en Visual Basic\) de la propriété <xref:System.AppDomain.CurrentDomain%2A?displayProperty=fullName> dans `Main()` pour obtenir une référence pour le domaine d'application par défaut.  
  
#### Pour illustrer des notifications des exceptions de première chance dans le domaine d'application  
  
1.  Créez un objet `Worker` dans le domaine d'application que vous avez créé dans la procédure précédente.  La classe `Worker` doit être publique et doit dériver de <xref:System.MarshalByRefObject>, comme indiqué dans l'exemple complet à la fin de cet article.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#4)]  
  
2.  Appelez une méthode de l'objet `Worker` qui lève une exception.  Dans cet exemple, la méthode `Thrower` est appelée deux fois.  La première fois, l'argument de méthode est `true`, la méthode intercepte donc sa propre exception.  La deuxième fois, l'argument est `false`, et la méthode `Main()` intercepte l'exception dans le domaine d'application par défaut.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#6)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#6)]  
  
3.  Placez le code dans la méthode `Thrower` à contrôler si la méthode gère sa propre exception.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#5)]  
  
## Exemple  
 L'exemple suivant crée un domaine d'application nommé `AD1` et ajoute un gestionnaire d'événements à l'événement <xref:System.AppDomain.FirstChanceException> du domaine d'application.  L'exemple crée une instance de la classe `Worker` dans le nouveau domaine d'application et appelle une méthode nommée `Thrower` qui lève une <xref:System.ArgumentException>.  Selon la valeur de son argument, la méthode intercepte l'exception ou ne parvient pas à la gérer.  
  
 Chaque fois que la méthode `Thrower` lève une exception dans `AD1`, l'événement <xref:System.AppDomain.FirstChanceException> est déclenché dans `AD1`, et le gestionnaire d'événements affiche un message.  Le runtime recherche ensuite un gestionnaire d'exceptions.  Dans le premier cas, le gestionnaire d'exceptions est recherché dans `AD1`.  Dans le deuxième cas, l'exception n'est pas gérée dans `AD1`, et est interceptée à la place dans le domaine d'application par défaut.  
  
> [!NOTE]
>  Le nom du domaine d'application par défaut est le même que celui du fichier exécutable.  
  
 Si vous ajoutez un gestionnaire pour l'événement <xref:System.AppDomain.FirstChanceException> au domaine d'application par défaut, l'événement est déclenché et géré avant que le domaine d'application par défaut ne gère l'exception.  Pour afficher cela, ajoutez le code C\# `AppDomain.CurrentDomain.FirstChanceException += FirstChanceException;` \(en Visual Basic, `AddHandler AppDomain.CurrentDomain.FirstChanceException, FirstChanceExceptio`n\) au début de `Main()`.  
  
 [!code-csharp[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#1)]
 [!code-vb[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#1)]  
  
## Compilation du code  
  
-   Cet exemple est une application en ligne de commande.  Pour compiler et exécuter ce code en [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], ajoutez le code C\# `Console.ReadLine();` \(en Visual Basic, `Console.ReadLine()`\) à la fin de `Main()`, afin d'empêcher la fermeture de la fenêtre de commande pour pouvoir lire la sortie.  
  
## Voir aussi  
 <xref:System.AppDomain.FirstChanceException>