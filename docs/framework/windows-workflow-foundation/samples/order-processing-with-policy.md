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
# <a name="order-processing-with-policy"></a><span data-ttu-id="70d29-102">Traitement des commandes avec une stratégie</span><span class="sxs-lookup"><span data-stu-id="70d29-102">Order Processing with Policy</span></span>
<span data-ttu-id="70d29-103">L'exemple de stratégie du traitement des commandes présente quelques-unes des fonctionnalités clés contenues dans le [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] de Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="70d29-103">The Order Processing Policy sample demonstrates some of the key features introduced in the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] of the Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="70d29-104">Les fonctionnalités suivantes du moteur de règles WF sont nouvelles :</span><span class="sxs-lookup"><span data-stu-id="70d29-104">The following functionality is new for the WF rules engine:</span></span>  
  
-   <span data-ttu-id="70d29-105">Prise en charge de la surcharge d'opérateur</span><span class="sxs-lookup"><span data-stu-id="70d29-105">Support for operator overloading.</span></span>  
  
-   <span data-ttu-id="70d29-106">Prise en charge de l'opérateur `new` permettant aux utilisateurs de créer de nouveaux objets et tableaux à partir de règles WF.</span><span class="sxs-lookup"><span data-stu-id="70d29-106">Support for the `new` operator, allowing users to create new objects and arrays from WF rules.</span></span>  
  
-   <span data-ttu-id="70d29-107">Prise en charge des méthodes d'extension permettant aux utilisateurs d'appeler ces méthodes à partir de règles WF compatibles avec les styles d'encodage C#.</span><span class="sxs-lookup"><span data-stu-id="70d29-107">Support for extension methods to make the user experience in calling extension methods from WF rules compatible with C# coding styles.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70d29-108">Cet exemple requiert l'installation et l'exécution du [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="70d29-108">This sample requires that [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] is installed to build and run.</span></span> [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]<span data-ttu-id="70d29-109"> est requis pour ouvrir le projet et les fichiers solution.</span><span class="sxs-lookup"><span data-stu-id="70d29-109"> is required to open the project and solution files.</span></span>  
  
 <span data-ttu-id="70d29-110">L'exemple présente un projet `OrderProcessingPolicy` contenant une commande client composée d'une liste numérotée d'éléments disponibles et d'un code postal.</span><span class="sxs-lookup"><span data-stu-id="70d29-110">The sample demonstrates an `OrderProcessingPolicy` project in which a customer order, which consists of a numbered list of available items and a zip code, is entered.</span></span> <span data-ttu-id="70d29-111">Le traitement de cette commande aboutit si les deux entrées sont correctes ; dans le cas contraire, la stratégie crée des objets d'erreur en utilisant un opérateur `+` surchargé et une méthode d'extension prédéfinie afin d'informer l'utilisateur de ces erreurs.</span><span class="sxs-lookup"><span data-stu-id="70d29-111">The order is processed successfully if both entries are correct; otherwise, the policy creates error objects, utilizing an overloaded `+` operator and a predefined extension method to inform the user of the errors.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="70d29-112">méthodes d’extension, consultez [spécification c# Version 3.0](http://go.microsoft.com/fwlink/?LinkId=95402).</span><span class="sxs-lookup"><span data-stu-id="70d29-112"> extension methods, see [C# Version 3.0 Specification](http://go.microsoft.com/fwlink/?LinkId=95402).</span></span>  
  
 <span data-ttu-id="70d29-113">Cet exemple est composé des projets suivants :</span><span class="sxs-lookup"><span data-stu-id="70d29-113">The sample is comprised of the following projects:</span></span>  
  
-   `OrderErrorLibrary`  
  
     <span data-ttu-id="70d29-114">La bibliothèque `OrderErrorLibrary` définit les classes `OrderError` et `OrderErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="70d29-114">The `OrderErrorLibrary` is a class library that defines `OrderError` and `OrderErrorCollection` classes.</span></span> <span data-ttu-id="70d29-115">Une instance `OrderError` est créée lorsqu'une entrée non valide est indiquée.</span><span class="sxs-lookup"><span data-stu-id="70d29-115">An `OrderError` instance is created when an invalid input is entered.</span></span> <span data-ttu-id="70d29-116">La bibliothèque fournit également une méthode d'extension pour la classe `OrderErrorCollection` qui génère la propriété `ErrorText` sur tous les objets `OrderError` de `OrderErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="70d29-116">The library also provides an extension method on the `OrderErrorCollection` class that outputs the `ErrorText` property on all `OrderError` objects in the `OrderErrorCollection`.</span></span>  
  
-   `OrderProcessingPolicy`  
  
     <span data-ttu-id="70d29-117">Le projet `OrderProcessingPolicy` est une application console WF qui définit une activité `PolicyFromFile` unique.</span><span class="sxs-lookup"><span data-stu-id="70d29-117">The `OrderProcessingPolicy` project is a WF console application that defines a single `PolicyFromFile` activity.</span></span> <span data-ttu-id="70d29-118">L'activité contient les règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="70d29-118">The activity has the following rules:</span></span>  
  
    -   `invalidItemNum`  
  
         <span data-ttu-id="70d29-119">Cette règle assure que le numéro d'élément est compris entre 1 et 6 (inclus).</span><span class="sxs-lookup"><span data-stu-id="70d29-119">This rule validates that the item number is between 1 and 6, inclusive.</span></span> <span data-ttu-id="70d29-120">Si le numéro est compris dans cette fourchette, la règle ne fait rien (excepté des impressions dans la console).</span><span class="sxs-lookup"><span data-stu-id="70d29-120">If the item number is within the valid range, the rule does nothing (other than printing to the console).</span></span> <span data-ttu-id="70d29-121">Dans le cas contraire, `invalidItemNum` elle effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="70d29-121">If the item number is not between 1 and 6, the `invalidItemNum` rule does the following:</span></span>  
  
        1.  <span data-ttu-id="70d29-122">Elle crée un objet `OrderError` en lui transmettant le numéro d'élément indiqué et définit les propriétés `ErrorText` et `CustomerName` dans cet objet.</span><span class="sxs-lookup"><span data-stu-id="70d29-122">Creates a new `OrderError` object, passing it the item number entered, and sets the `ErrorText` and `CustomerName` properties on the object.</span></span>  
  
        2.  <span data-ttu-id="70d29-123">Elle crée un objet `invalidItemNumErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="70d29-123">Creates an `invalidItemNumErrorCollection` object.</span></span>  
  
        3.  <span data-ttu-id="70d29-124">Elle ajoute l'instance `OrderError` nouvellement créée à l'objet `invalidItemNumErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="70d29-124">Adds the newly-created `OrderError` instance to the `invalidItemNumErrorCollection`.</span></span>  
  
         <span data-ttu-id="70d29-125">Cette opération prouve la prise en charge de l'opérateur `new`, qui permet d'instancier des objets à l'intérieur de règles.</span><span class="sxs-lookup"><span data-stu-id="70d29-125">This demonstrates support for the `new` operator, with which you can instantiate objects inside rules.</span></span>  
  
    -   `invalidZip`  
  
         <span data-ttu-id="70d29-126">Cette règle valide que le code postal comporte 5 chiffres, et qu'il est compris dans la plage 600 à 99998.</span><span class="sxs-lookup"><span data-stu-id="70d29-126">This rule validates that the zip code has 5 digits, and is within the range 600 to 99998.</span></span> <span data-ttu-id="70d29-127">Si le code postal est compris dans cette plage, la règle ne fait rien (excepté l'impression sur la console).</span><span class="sxs-lookup"><span data-stu-id="70d29-127">If the zip code is within the valid range, the rule does nothing (other than printing to the console).</span></span> <span data-ttu-id="70d29-128">S'il contient moins de 5 chiffres et n'est pas compris entre 00600 et 99998, la règle `invalidZip` effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="70d29-128">If the length of the zip code is less than 5, or the zip code is not between 00600 and 99998, the `invalidZip` rule does the following:</span></span>  
  
        1.  <span data-ttu-id="70d29-129">Elle crée un objet `OrderError` en lui transmettant le code postal indiqué et définit les propriétés `ErrorText` et `CustomerName` dans cet objet.</span><span class="sxs-lookup"><span data-stu-id="70d29-129">Creates an `OrderError` object, passing it the zip code entered, and sets the `ErrorText` and `CustomerName` properties on the object.</span></span>  
  
        2.  <span data-ttu-id="70d29-130">Elle crée un objet `invalidZipCodeErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="70d29-130">Creates an `invalidZipCodeErrorCollection` object.</span></span>  
  
        3.  <span data-ttu-id="70d29-131">Elle ajoute l'instance `OrderError` créée au nouvel objet `invalidZipCodeErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="70d29-131">Adds the newly-created `OrderError` instance to the newly-created `invalidZipCodeErrorCollection`.</span></span>  
  
         <span data-ttu-id="70d29-132">Cette règle prouve à nouveau la prise en charge de l'opérateur `new`, qui permet d'instancier des objets à l'intérieur de règles.</span><span class="sxs-lookup"><span data-stu-id="70d29-132">This rule again demonstrates support for the `new` operator, which allows you to instantiate objects inside rules.</span></span>  
  
    -   `displayErrors`  
  
         <span data-ttu-id="70d29-133">Cette règle vérifie si les deux règles précédentes ont ajouté des erreurs dans les deux objets de `OrderErrorCollection`, `invalidItemNumErrorCollection` et de `invalidIZipCodeErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="70d29-133">This rule checks to see if there were any errors added by the previous two rules in the two `OrderErrorCollection` objects `invalidItemNumErrorCollection` and `invalidIZipCodeErrorCollection`.</span></span> <span data-ttu-id="70d29-134">Si c'est le cas (`invalidItemNumErrorCollection` ou `invalidZipCodeErrorCollection` n'a pas la valeur `null`), la règle effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="70d29-134">If there were errors (either `invalidItemNumErrorCollection` or `invalidZipCodeErrorCollection` is not `null`), the rule does the following:</span></span>  
  
        1.  <span data-ttu-id="70d29-135">Appelle surchargées `+` opérateur pour copier le contenu de `invalidItemNumErrorCollection` et `invalidZipCodeErrorCollection` à un `invalidOrdersCollection``OrderErrorCollection` instance.</span><span class="sxs-lookup"><span data-stu-id="70d29-135">Calls the overloaded `+` operator to copy the contents of `invalidItemNumErrorCollection` and `invalidZipCodeErrorCollection` to an `invalidOrdersCollection``OrderErrorCollection` instance.</span></span>  
  
        2.  <span data-ttu-id="70d29-136">Elle appelle la méthode d'extension `PrintOrderErrors` dans l'instance `invalidOrdersCollection` et génère la propriété `ErrorText` dans tous les objets `orderError` de l'instance `invalidOrdersCollection`.</span><span class="sxs-lookup"><span data-stu-id="70d29-136">Calls the `PrintOrderErrors` extension method on `invalidOrdersCollection` and outputs the `ErrorText` property on all `orderError` objects in `invalidOrdersCollection`.</span></span>  
  
 <span data-ttu-id="70d29-137">L'opérateur `+` surchargé de `OrderErrorCollection` est défini dans la classe `OrderErrorCollection`, au sein du projet `OrderErrorLibrary`.</span><span class="sxs-lookup"><span data-stu-id="70d29-137">The overloaded operator `+` on the `OrderErrorCollection` is defined in the `OrderErrorCollection` class, in the `OrderErrorLibrary` project.</span></span> <span data-ttu-id="70d29-138">Il utilise deux objets `OrderErrorCollection` et les fusionne en un seul objet `OrderErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="70d29-138">It takes two `OrderErrorCollection` objects and combines them into one `OrderErrorCollection` object.</span></span>  
  
 <span data-ttu-id="70d29-139">La méthode d'extension `PrintOrderErrors` est également définie dans le projet `OrderErrorLibrary`.</span><span class="sxs-lookup"><span data-stu-id="70d29-139">The `PrintOrderErrors` extension method is also defined in the `OrderErrorLibrary` project.</span></span> <span data-ttu-id="70d29-140">Les méthodes d'extension constituent une nouvelle fonctionnalité C# qui permet aux développeurs d'ajouter de nouvelles méthodes au contrat public d'un type CLR existant, sans avoir à dériver une classe ou à recompiler le type d'origine.</span><span class="sxs-lookup"><span data-stu-id="70d29-140">Extension methods are a new C# feature that enables developers to add new methods to the public contract of an existing CLR type, without having to derive a class from it or recompile the original type.</span></span>  
  
 <span data-ttu-id="70d29-141">Lorsque vous exécutez l'exemple vous êtes invité à entrer un nom, le numéro de l'élément à acheter, ainsi qu'un code postal.</span><span class="sxs-lookup"><span data-stu-id="70d29-141">When you run the sample you are prompted to enter a name, the item number of the item to be purchased, and a zip code.</span></span> <span data-ttu-id="70d29-142">Ces informations sont ensuite vérifiées par les règles définies dans l'activité de stratégie.</span><span class="sxs-lookup"><span data-stu-id="70d29-142">This information is then verified by the rules defined in the policy activity.</span></span> <span data-ttu-id="70d29-143">L'exemple suivant illustre une sortie du programme.</span><span class="sxs-lookup"><span data-stu-id="70d29-143">The following is sample output from the program.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="70d29-144">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="70d29-144">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="70d29-145">Ouvrez le fichier projet OrderProcessingPolicy.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="70d29-145">Open the OrderProcessingPolicy.sln project file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="70d29-146">La solution contient deux projets différents : `OrderErrorLibrary` et `OrderProcessingPolicy`.</span><span class="sxs-lookup"><span data-stu-id="70d29-146">There are two different projects in the solution: `OrderErrorLibrary` and `OrderProcessingPolicy`.</span></span> <span data-ttu-id="70d29-147">Le projet `OrderProcessingPolicy` utilise les classes et les méthodes définies dans le projet `OrderErrorLibrary`.</span><span class="sxs-lookup"><span data-stu-id="70d29-147">The `OrderProcessingPolicy` project uses classes and methods defined in the `OrderErrorLibrary`.</span></span>  
  
3.  <span data-ttu-id="70d29-148">Générez tous les projets.</span><span class="sxs-lookup"><span data-stu-id="70d29-148">Build all projects.</span></span>  
  
4.  <span data-ttu-id="70d29-149">Cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="70d29-149">Click **Run**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="70d29-150">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="70d29-150">The samples may already be installed on your computer.</span></span> <span data-ttu-id="70d29-151">Recherchez le répertoire (par défaut) suivant avant de continuer :</span><span class="sxs-lookup"><span data-stu-id="70d29-151">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="70d29-152">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="70d29-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="70d29-153">Cet exemple se trouve dans le répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="70d29-153">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\OrderProcessingPolicy`