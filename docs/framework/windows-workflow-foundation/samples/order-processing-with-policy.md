---
title: "Traitement des commandes avec une stratégie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66833724-dc36-4fad-86b0-59ffeaa3ba6a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4aaab8fca4693f6b253d48f066e644cc76637241
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="order-processing-with-policy"></a>Traitement des commandes avec une stratégie
L'exemple de stratégie du traitement des commandes présente quelques-unes des fonctionnalités clés contenues dans le [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] de Windows Workflow Foundation (WF). Les fonctionnalités suivantes du moteur de règles WF sont nouvelles :  
  
-   Prise en charge de la surcharge d'opérateur  
  
-   Prise en charge de l'opérateur `new` permettant aux utilisateurs de créer de nouveaux objets et tableaux à partir de règles WF.  
  
-   Prise en charge des méthodes d'extension permettant aux utilisateurs d'appeler ces méthodes à partir de règles WF compatibles avec les styles d'encodage C#.  
  
> [!NOTE]
>  Cet exemple requiert l'installation et l'exécution du [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]. [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] est requis pour ouvrir le projet et les fichiers solution.  
  
 L'exemple présente un projet `OrderProcessingPolicy` contenant une commande client composée d'une liste numérotée d'éléments disponibles et d'un code postal. Le traitement de cette commande aboutit si les deux entrées sont correctes ; dans le cas contraire, la stratégie crée des objets d'erreur en utilisant un opérateur `+` surchargé et une méthode d'extension prédéfinie afin d'informer l'utilisateur de ces erreurs.  
  
> [!NOTE]
>  [!INCLUDE[crabout](../../../../includes/crabout-md.md)]méthodes d’extension, consultez [spécification c# Version 3.0](http://go.microsoft.com/fwlink/?LinkId=95402).  
  
 Cet exemple est composé des projets suivants :  
  
-   `OrderErrorLibrary`  
  
     La bibliothèque `OrderErrorLibrary` définit les classes `OrderError` et `OrderErrorCollection`. Une instance `OrderError` est créée lorsqu'une entrée non valide est indiquée. La bibliothèque fournit également une méthode d'extension pour la classe `OrderErrorCollection` qui génère la propriété `ErrorText` sur tous les objets `OrderError` de `OrderErrorCollection`.  
  
-   `OrderProcessingPolicy`  
  
     Le projet `OrderProcessingPolicy` est une application console WF qui définit une activité `PolicyFromFile` unique. L'activité contient les règles suivantes :  
  
    -   `invalidItemNum`  
  
         Cette règle assure que le numéro d'élément est compris entre 1 et 6 (inclus). Si le numéro est compris dans cette fourchette, la règle ne fait rien (excepté des impressions dans la console). Dans le cas contraire, `invalidItemNum` elle effectue les opérations suivantes :  
  
        1.  Elle crée un objet `OrderError` en lui transmettant le numéro d'élément indiqué et définit les propriétés `ErrorText` et `CustomerName` dans cet objet.  
  
        2.  Elle crée un objet `invalidItemNumErrorCollection`.  
  
        3.  Elle ajoute l'instance `OrderError` nouvellement créée à l'objet `invalidItemNumErrorCollection`.  
  
         Cette opération prouve la prise en charge de l'opérateur `new`, qui permet d'instancier des objets à l'intérieur de règles.  
  
    -   `invalidZip`  
  
         Cette règle valide que le code postal comporte 5 chiffres, et qu'il est compris dans la plage 600 à 99998. Si le code postal est compris dans cette plage, la règle ne fait rien (excepté l'impression sur la console). S'il contient moins de 5 chiffres et n'est pas compris entre 00600 et 99998, la règle `invalidZip` effectue les opérations suivantes :  
  
        1.  Elle crée un objet `OrderError` en lui transmettant le code postal indiqué et définit les propriétés `ErrorText` et `CustomerName` dans cet objet.  
  
        2.  Elle crée un objet `invalidZipCodeErrorCollection`.  
  
        3.  Elle ajoute l'instance `OrderError` créée au nouvel objet `invalidZipCodeErrorCollection`.  
  
         Cette règle prouve à nouveau la prise en charge de l'opérateur `new`, qui permet d'instancier des objets à l'intérieur de règles.  
  
    -   `displayErrors`  
  
         Cette règle vérifie si les deux règles précédentes ont ajouté des erreurs dans les deux objets de `OrderErrorCollection`, `invalidItemNumErrorCollection` et de `invalidIZipCodeErrorCollection`. Si c'est le cas (`invalidItemNumErrorCollection` ou `invalidZipCodeErrorCollection` n'a pas la valeur `null`), la règle effectue les opérations suivantes :  
  
        1.  Appelle surchargées `+` opérateur pour copier le contenu de `invalidItemNumErrorCollection` et `invalidZipCodeErrorCollection` à un `invalidOrdersCollection``OrderErrorCollection` instance.  
  
        2.  Elle appelle la méthode d'extension `PrintOrderErrors` dans l'instance `invalidOrdersCollection` et génère la propriété `ErrorText` dans tous les objets `orderError` de l'instance `invalidOrdersCollection`.  
  
 L'opérateur `+` surchargé de `OrderErrorCollection` est défini dans la classe `OrderErrorCollection`, au sein du projet `OrderErrorLibrary`. Il utilise deux objets `OrderErrorCollection` et les fusionne en un seul objet `OrderErrorCollection`.  
  
 La méthode d'extension `PrintOrderErrors` est également définie dans le projet `OrderErrorLibrary`. Les méthodes d'extension constituent une nouvelle fonctionnalité C# qui permet aux développeurs d'ajouter de nouvelles méthodes au contrat public d'un type CLR existant, sans avoir à dériver une classe ou à recompiler le type d'origine.  
  
 Lorsque vous exécutez l'exemple vous êtes invité à entrer un nom, le numéro de l'élément à acheter, ainsi qu'un code postal. Ces informations sont ensuite vérifiées par les règles définies dans l'activité de stratégie. L'exemple suivant illustre une sortie du programme.  
  
```  
Please enter your name: John  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 1  
  
Please enter your 5-Digit zip code: 98102  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Thank you for your order, it has been processed.  
  
Workflow Completed  
Another Order? (Y/N): y  
  
Please enter your name: Joel  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 8  
  
Please enter your 5-Digit zip code: 0000  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Your order contains the following error(s)  
  
Error: No item number found. Please choose an available item.  
Error: Invalid zip code. Please choose a zip code between 00600 and 99998.  
  
Workflow Completed  
Another Order? (Y/N): n  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Ouvrez le fichier projet OrderProcessingPolicy.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  La solution contient deux projets différents : `OrderErrorLibrary` et `OrderProcessingPolicy`. Le projet `OrderProcessingPolicy` utilise les classes et les méthodes définies dans le projet `OrderErrorLibrary`.  
  
3.  Générez tous les projets.  
  
4.  Cliquez sur **Exécuter**.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer :  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant :  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\OrderProcessingPolicy`