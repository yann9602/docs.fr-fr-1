---
title: "Comment&#160;: s&#39;abonner et annuler l&#39;abonnement &#224; des &#233;v&#233;nements (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "éditeur de code, gestionnaires d'événements"
  - "gestionnaires d'événements (C#), créer"
  - "événements (C#), créer à l'aide de l'interface IDE"
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# Comment&#160;: s&#39;abonner et annuler l&#39;abonnement &#224; des &#233;v&#233;nements (Guide de programmation C#)
Vous vous abonnez à un événement qui est publié par une autre classe lorsque vous souhaitez écrire un code personnalisé qui est appelé lorsque cet événement est déclenché.  Par exemple, vous pouvez vous abonner à l'événement `click` d'un bouton pour que votre application exécute une action lorsque l'utilisateur clique sur le bouton.  
  
### Pour s'abonner des événements à l'aide de l'IDE Visual Studio  
  
1.  Si la fenêtre **Propriétés** n'est pas visible, en mode **Design**, cliquez avec le bouton droit sur le formulaire ou le contrôle pour lequel vous souhaitez créer un gestionnaire d'événements et sélectionnez **Propriétés**.  
  
2.  Dans la partie supérieure de la fenêtre **Propriétés**, cliquez sur le bouton **Événements**.  
  
3.  Double\-cliquez sur l'événement que vous souhaitez créer, par exemple l'événement `Load`.  
  
     [!INCLUDE[csprcs](../../../csharp/includes/csprcs-md.md)] crée une méthode de gestionnaire d'événements vide et l'ajoute à votre code.  Vous pouvez également ajouter manuellement le code en mode **Code**.  Par exemple, les lignes de code ci\-après déclarent une méthode de gestionnaire d'événements qui est appelée lorsque la classe `Form` déclenche l'événement `Load`.  
  
     [!code-cs[csProgGuideEvents#11](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-subscribe-to-and-unsubscribe-from-events_1.cs)]  
  
     La ligne de code nécessaire pour s'abonner à l'événement est également générée automatiquement dans la méthode `InitializeComponent` du fichier Form1.Designer.cs de votre projet.  Elle se présente comme suit :  
  
    ```  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### Pour s'abonner à des événements par programme  
  
1.  Définissez une méthode de gestionnaire d'événements dont la signature correspond à la signature du délégué pour l'événement.  Par exemple, si l'événement est basé sur le type délégué <xref:System.EventHandler>, le code suivant représente le stub de méthode :  
  
    ```  
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2.  Utilisez l'opérateur d'assignation d'addition \(`+=`\) pour attacher votre gestionnaire d'événements à l'événement.  Dans l'exemple suivant, supposez qu'un objet intitulé `publisher` possède un événement nommé `RaiseCustomEvent`.  Notez que la classe d'abonné a besoin d'une référence à la classe d'éditeur pour s'abonner à ses événements.  
  
    ```  
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     Notez que la syntaxe précédente est nouvelle dans C\# 2.0.  Elle équivaut exactement à la syntaxe C\# 1.0 dans laquelle le délégué d'encapsulation doit être explicitement créé à l'aide du mot clé `new` :  
  
    ```  
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     Il est possible d'ajouter un gestionnaire d'événements à l'aide d'une expression lambda.  
  
    ```  
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
        this.Click += (s,e) => { MessageBox.Show(  
           ((MouseEventArgs)e).Location.ToString());};  
    }  
    ```  
  
     Pour plus d'informations, consultez [Comment : utiliser des expressions lambda en dehors de LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).  
  
### Pour s'abonner des événements en utilisant une méthode anonyme  
  
-   Si vous ne devez pas annuler l'abonnement à un événement ultérieurement, vous pouvez utiliser l'opérateur d'assignation d'addition \(`+=`\) pour attacher une méthode anonyme à l'événement.  Dans l'exemple ci\-après, supposez qu'un objet intitulé `publisher` possède un événement nommé `RaiseCustomEvent`  et qu'une classe `CustomEventArgs` a également été définie pour retenir quelque type d'informations spécialisées sur l'événement.  Notez que la classe d'abonné a besoin d'une référence à `publisher` pour s'abonner à ses événements.  
  
    ```  
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     Il importe de noter qu'il n'est pas aisé d'annuler un abonnement à un événement si vous avez utilisé une fonction anonyme pour vous y abonner.  Pour annuler un abonnement dans ce cas, vous devez revenir dans le code où vous vous abonnez à l'événement, stocker la méthode anonyme dans une variable de délégué, puis ajouter le délégué à l'événement.  En général, nous recommandons de ne pas utiliser de fonctions anonymes pour les abonnements aux événements que vous devez annuler ultérieurement dans votre code.  Pour plus d'informations sur les fonctions anonymes, consultez [Fonctions anonymes](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## Annulation d'un abonnement  
 Annulez un abonnement à l'événement pour empêcher votre gestionnaire d'événements d'être appelé lorsque l'événement est déclenché.  Pour empêcher toute fuite de ressources, vous devez annuler un abonnement aux événements avant d'éliminer un objet d'abonné.  Tant que vous n'avez pas annulé l'abonnement à un événement, le délégué multicast sous\-jacent à l'événement de l'objet d'édition possède une référence au délégué qui encapsule le gestionnaire d'événements de l'abonné.  Tant que l'objet de l'édition détient cette référence, le garbage collection ne supprimera pas votre objet d'abonné.  
  
#### Pour annuler un abonnement à un événement  
  
-   Utilisez l'opérateur d'assignation de soustraction \(`-=`\) pour annuler un abonnement à un événement :  
  
    ```  
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     Lorsque tous les abonnés ont annulé leur abonnement à un événement, l'instance d'événement de la classe d'éditeur est `null`.  
  
## Voir aussi  
 [Événements](../../../csharp/programming-guide/events/index.md)   
 [event](../../../csharp/language-reference/keywords/event.md)   
 [Comment : publier des événements conformes aux indications du .NET Framework](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)   
 [\-\=, opérateur](../../../csharp/language-reference/operators/subtraction-assignment-operator-1.md)   
 [\+\=, opérateur](../../../csharp/language-reference/operators/addition-assignment-operator.md)