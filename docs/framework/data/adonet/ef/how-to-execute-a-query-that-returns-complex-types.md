---
title: "Comment : exécuter une requête qui retourne les types complexes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a499c8cf9caeac480e09d7c965032db2d9fefec4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a><span data-ttu-id="63e98-102">Comment : exécuter une requête qui retourne les types complexes</span><span class="sxs-lookup"><span data-stu-id="63e98-102">How to: Execute a Query that Returns Complex Types</span></span>
<span data-ttu-id="63e98-103">Cette rubrique indique comment exécuter une requête [!INCLUDE[esql](../../../../../includes/esql-md.md)] qui retourne des objets de type d'entité qui contiennent une propriété d'un type complexe.</span><span class="sxs-lookup"><span data-stu-id="63e98-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that returns entity type objects that contain a property of a complex type.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="63e98-104">Pour exécuter le code de cet exemple</span><span class="sxs-lookup"><span data-stu-id="63e98-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="63e98-105">Ajouter le [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) à votre projet et configurer votre projet pour utiliser le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63e98-105">Add the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="63e98-106">Pour plus d’informations, consultez [Comment : utiliser l’Assistant Entity Data Model](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="63e98-106">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="63e98-107">Dans la page de codes de votre application, ajoutez les instructions `using` (`Imports` en Visual Basic) suivantes :</span><span class="sxs-lookup"><span data-stu-id="63e98-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  <span data-ttu-id="63e98-108">Double-cliquez sur le fichier .edmx pour afficher le modèle dans le [fenêtre Explorateur de modèles](http://msdn.microsoft.com/en-us/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd) du Concepteur d’entités.</span><span class="sxs-lookup"><span data-stu-id="63e98-108">Double click the .edmx file to display the model in the [Model Browser window](http://msdn.microsoft.com/en-us/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd) of the Entity Designer.</span></span> <span data-ttu-id="63e98-109">Sur l’aire du Concepteur d’entités, sélectionnez le `Email` et `Phone` propriétés de la `Contact` type d’entité, puis avec le bouton droit et sélectionnez **refactoriser en nouveau Type complexe**.</span><span class="sxs-lookup"><span data-stu-id="63e98-109">On the Entity Designer surface, select the `Email` and `Phone` properties of the `Contact` entity type, then right-click and select **Refactor into New Complex Type**.</span></span>  
  
4.  <span data-ttu-id="63e98-110">Un nouveau type complexe avec le `Email` et `Phone` propriétés est ajouté à la **Explorateur de modèles**.</span><span class="sxs-lookup"><span data-stu-id="63e98-110">A new complex type with the selected `Email` and `Phone` properties is added to the **Model Browser**.</span></span> <span data-ttu-id="63e98-111">Le type complexe reçoit un nom par défaut : Renommez le type en `EmailPhone` dans les **propriétés** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="63e98-111">The complex type is given a default name: rename the type to `EmailPhone` in the **Properties** window.</span></span> <span data-ttu-id="63e98-112">Une nouvelle propriété `ComplexProperty` est également ajoutée au type d'entité `Contact`.</span><span class="sxs-lookup"><span data-stu-id="63e98-112">Also, a new `ComplexProperty` property is added to the `Contact` entity type.</span></span> <span data-ttu-id="63e98-113">Renommez la propriété en `EmailPhoneComplexType.`.</span><span class="sxs-lookup"><span data-stu-id="63e98-113">Rename the property to `EmailPhoneComplexType.`</span></span>  
  
     <span data-ttu-id="63e98-114">Pour plus d’informations sur la création et modification des types complexes à l’aide de l’Assistant Entity Data Model, consultez [Comment : refactoriser les propriétés existantes dans une propriété de Type complexe](http://msdn.microsoft.com/en-us/5b2eb3b3-693d-42cb-b43a-405812d677eb) et [Comment : créer et modifier les Types complexes](http://msdn.microsoft.com/en-us/afb8e206-0ffe-4597-b6d4-6ab566897e1d).</span><span class="sxs-lookup"><span data-stu-id="63e98-114">For information about creating and modifying complex types by using the Entity Data Model Wizard, see [How to: Refactor Existing Properties into a Complex Type Property](http://msdn.microsoft.com/en-us/5b2eb3b3-693d-42cb-b43a-405812d677eb) and [How to: Create and Modify Complex Types](http://msdn.microsoft.com/en-us/afb8e206-0ffe-4597-b6d4-6ab566897e1d).</span></span>  
  
## <a name="example"></a><span data-ttu-id="63e98-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="63e98-115">Example</span></span>  
 <span data-ttu-id="63e98-116">L’exemple suivant exécute une requête qui retourne une collection de `Contact` des objets et affiche deux propriétés de la `Contact` objets : `ContactID` et les valeurs de la `EmailPhoneComplexType` type complexe.</span><span class="sxs-lookup"><span data-stu-id="63e98-116">The following example executes a query that returns a collection of `Contact` objects and displays two properties of the `Contact` objects: `ContactID` and the values of the `EmailPhoneComplexType` complex type.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
