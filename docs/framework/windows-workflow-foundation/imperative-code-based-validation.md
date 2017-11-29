---
title: "Validation basée sur le code impératif"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae12537c-455e-42b1-82f4-cea4c46c023e
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5b9919c2919bf670396dc4af7d17d7087f9b4908
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="imperative-code-based-validation"></a><span data-ttu-id="474ee-102">Validation basée sur le code impératif</span><span class="sxs-lookup"><span data-stu-id="474ee-102">Imperative Code-Based Validation</span></span>
<span data-ttu-id="474ee-103">La validation basée sur le code impératif offre un moyen simple de valider une activité ainsi que les activités dérivées de <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity> et <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="474ee-103">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="474ee-104">Le code de validation est ajouté à l'activité qui détermine les erreurs ou avertissements de validation ajoutés à l'activité.</span><span class="sxs-lookup"><span data-stu-id="474ee-104">Validation code that determines any validation errors or warnings is added to the activity.</span></span>  
  
## <a name="using-code-based-validation"></a><span data-ttu-id="474ee-105">Utilisation de la validation basée sur le code</span><span class="sxs-lookup"><span data-stu-id="474ee-105">Using Code-Based Validation</span></span>  
 <span data-ttu-id="474ee-106">La validation basée sur le code est prise en charge par les activités dérivées de <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity> et <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="474ee-106">Code-based validation is supported by activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="474ee-107">Le code de validation peut être placé dans la substitution <xref:System.Activities.CodeActivity.CacheMetadata%2A>, et les erreurs ou avertissements de validation peuvent être ajoutés à l'argument de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="474ee-107">Validation code can be placed in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override, and validation errors or warnings can be added to the metadata argument.</span></span> <span data-ttu-id="474ee-108">Dans l’exemple suivant, issu de la [une Validation de base](../../../docs/framework/windows-workflow-foundation/samples/basic-validation.md) exemple, si le `Cost` est supérieure à la `Price`, une erreur de validation est ajoutée aux métadonnées.</span><span class="sxs-lookup"><span data-stu-id="474ee-108">In the following example, taken from the [Basic Validation](../../../docs/framework/windows-workflow-foundation/samples/basic-validation.md) sample, if the `Cost` is greater than the `Price`, a validation error is added to the metadata.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="474ee-109">Notez que `Cost` et `Price` ne sont pas des arguments de l'activité, mais sont des propriétés définies au moment du design.</span><span class="sxs-lookup"><span data-stu-id="474ee-109">Note that `Cost` and `Price` are not arguments to the activity, but are properties that are set at design time.</span></span> <span data-ttu-id="474ee-110">C'est pourquoi leurs valeurs peuvent être validées dans la substitution <xref:System.Activities.CodeActivity.CacheMetadata%2A>.</span><span class="sxs-lookup"><span data-stu-id="474ee-110">That is why their values can be validated in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="474ee-111">La valeur des données diffusées via un argument ne peut pas être validée au moment du design, car les données ne sont diffusées qu'au moment de l'exécution, mais des arguments d'activité peuvent être validés pour vérifier qu'ils sont liés à l'aide de l'attribut `RequiredArgument` et des groupes surchargés.</span><span class="sxs-lookup"><span data-stu-id="474ee-111">The value of the data flowing through an argument cannot be validated at design time because the data does not flow until run time, but activity arguments can be validated to ensure that they are bound by using the `RequiredArgument` attribute and overload groups.</span></span> <span data-ttu-id="474ee-112">Cet exemple de code voit l'attribut `RequiredArgument` de l'argument `Description`, et s'il n'est pas lié, une erreur de validation est générée.</span><span class="sxs-lookup"><span data-stu-id="474ee-112">This example code sees the `RequiredArgument` attribute for the `Description` argument, and if it is not bound then a validation error is generated.</span></span> <span data-ttu-id="474ee-113">Les arguments obligatoires sont traités dans [requis des Arguments et des groupes surchargés](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md).</span><span class="sxs-lookup"><span data-stu-id="474ee-113">Required arguments are covered in [Required Arguments and Overload Groups](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md).</span></span>  
  
```csharp  
public sealed class CreateProduct : CodeActivity  
{  
    public double Price { get; set; }  
    public double Cost { get; set; }  
  
    // [RequiredArgument] attribute will generate a validation error   
    // if the Description argument is not set.  
    [RequiredArgument]  
    public InArgument<string> Description { get; set; }  
  
    protected override void CacheMetadata(CodeActivityMetadata metadata)  
    {  
        base.CacheMetadata(metadata);  
        // Determine when the activity has been configured in an invalid way.  
        if (this.Cost > this.Price)  
        {  
            // Add a validation error with a custom message.  
            metadata.AddValidationError("The Cost must be less than or equal to the Price.");  
        }  
    }  
  
    protected override void Execute(CodeActivityContext context)  
    {  
        // Not needed for the sample.  
    }  
}  
```  
  
 <span data-ttu-id="474ee-114">Par défaut, une erreur de validation est ajoutée aux métadonnées lorsque <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> est appelé.</span><span class="sxs-lookup"><span data-stu-id="474ee-114">By default, a validation error is added to the metadata when <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> is called.</span></span> <span data-ttu-id="474ee-115">Pour ajouter un avertissement de validation, utilisez la surcharge <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> qui prend <xref:System.Activities.Validation.ValidationError> et spécifiez que <xref:System.Activities.Validation.ValidationError> représente un avertissement en définissant la propriété <xref:System.Activities.Validation.ValidationError.IsWarning%2A>.</span><span class="sxs-lookup"><span data-stu-id="474ee-115">To add a validation warning, use the <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> overload that takes a <xref:System.Activities.Validation.ValidationError>, and specify that the <xref:System.Activities.Validation.ValidationError> represents a warning by setting the <xref:System.Activities.Validation.ValidationError.IsWarning%2A> property.</span></span>  
  
 <span data-ttu-id="474ee-116">La validation a lieu lorsque, dans le Concepteur de Workflow, un workflow est modifié et que l'ensemble des erreurs ou avertissements de validation sont affichés.</span><span class="sxs-lookup"><span data-stu-id="474ee-116">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="474ee-117">La validation se produit également au moment de l'exécution lorsqu'un workflow est appelé et si des erreurs de validation se produisent, <xref:System.Activities.InvalidWorkflowException> est levée par la logique de validation par défaut.</span><span class="sxs-lookup"><span data-stu-id="474ee-117">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="474ee-118">appel de la validation et l’accès à des avertissements de validation ou d’erreurs, consultez [appel de Validation d’activité](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="474ee-118"> invoking validation and accessing any validation warnings or errors, see [Invoking Activity Validation](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span></span>  
  
 <span data-ttu-id="474ee-119">Toutes les exceptions levées à partir de <xref:System.Activities.CodeActivity.CacheMetadata%2A> ne sont pas traitées comme des erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="474ee-119">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="474ee-120">Ces exceptions ne seront pas détectées par l'appel à <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> et doivent être gérées par l'appelant.</span><span class="sxs-lookup"><span data-stu-id="474ee-120">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
 <span data-ttu-id="474ee-121">La validation basée sur le code est utile pour valider l’activité qui contient le code, mais elle n’offre pas de visibilité pour les autres activités du workflow.</span><span class="sxs-lookup"><span data-stu-id="474ee-121">Code-based validation is useful for validating the activity that contains the code, but it does not have visibility into the other activities in the workflow.</span></span> <span data-ttu-id="474ee-122">Validation de contraintes déclaratives offre la possibilité de valider les relations entre une activité et d’autres activités dans le flux de travail et est décrite dans le [contraintes déclaratives](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="474ee-122">Declarative constraints validation provides the ability to validate the relationships between an activity and other activities in the workflow, and is covered in the [Declarative Constraints](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md) topic.</span></span>
