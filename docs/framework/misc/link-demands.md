---
title: Demandes de liaison
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], demands
- demanded permissions
- permissions [.NET Framework], demands
- granting permissions, demands
- code access security, demands
- user demands for permission
- caller security checks
- link demands
ms.assetid: a33fd5f9-2de9-4653-a4f0-d9df25082c4d
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e59ae7b0c26106f19f5b14290047deb9b5f30c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="link-demands"></a><span data-ttu-id="587a5-102">Demandes de liaison</span><span class="sxs-lookup"><span data-stu-id="587a5-102">Link Demands</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="587a5-103">Une demande de liaison entraîne une vérification de sécurité pendant la compilation juste-à-temps. Seul l'assembly appelant immédiat de votre code est vérifié.</span><span class="sxs-lookup"><span data-stu-id="587a5-103">A link demand causes a security check during just-in-time compilation and checks only the immediate calling assembly of your code.</span></span> <span data-ttu-id="587a5-104">La liaison est établie quand le code est lié à une référence de type, y compris les références de pointeur fonction et les appels de méthode.</span><span class="sxs-lookup"><span data-stu-id="587a5-104">Linking occurs when your code is bound to a type reference, including function pointer references and method calls.</span></span> <span data-ttu-id="587a5-105">Si l'assembly appelant ne dispose pas des autorisations suffisantes pour établir une liaison avec votre code, la liaison n'est pas autorisée et une exception d'exécution est levée quand le code est chargé et exécuté.</span><span class="sxs-lookup"><span data-stu-id="587a5-105">If the calling assembly does not have sufficient permission to link to your code, the link is not allowed and a runtime exception is thrown when the code is loaded and run.</span></span> <span data-ttu-id="587a5-106">Les demandes de liaison peuvent être substituées dans les classes qui héritent de votre code.</span><span class="sxs-lookup"><span data-stu-id="587a5-106">Link demands can be overridden in classes that inherit from your code.</span></span>  
  
 <span data-ttu-id="587a5-107">Notez qu'un parcours de pile complet n'est pas exécuté avec ce type de demande et que votre code est toujours susceptible de subir des attaques malveillantes.</span><span class="sxs-lookup"><span data-stu-id="587a5-107">Note that a full stack walk is not performed with this type of demand and that your code is still susceptible to luring attacks.</span></span> <span data-ttu-id="587a5-108">Par exemple, si une méthode dans l’assembly A est protégée par une demande de liaison, un appelant direct dans l’assembly B est évalué en fonction des autorisations de l’Assembly B.  Toutefois, la demande de liaison n’évaluera pas une méthode dans l’assembly C si elle appelle indirectement la méthode dans l’assembly d’un à l’aide de la méthode dans l’assembly B. La demande de liaison spécifie qu'uniquement les autorisations appelants directs dans l’assembly appelant immédiat doivent posséder lier à votre code.</span><span class="sxs-lookup"><span data-stu-id="587a5-108">For example, if a method in assembly A is protected by a link demand, a direct caller in assembly B is evaluated based on the permissions of Assembly B.  However, the link demand will not evaluate a method in assembly C if it indirectly calls the method in assembly A using the method in assembly B. The link demand specifies only the permissions direct callers in the immediate calling assembly must have to link to your code.</span></span> <span data-ttu-id="587a5-109">Elle ne spécifie pas les autorisations que tous les appelants doivent avoir pour exécuter votre code.</span><span class="sxs-lookup"><span data-stu-id="587a5-109">It does not specify the permissions all callers must have to run your code.</span></span>  
  
 <span data-ttu-id="587a5-110">Les modificateurs de parcours de pile <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A> et <xref:System.Security.CodeAccessPermission.PermitOnly%2A> n'affectent pas l'évaluation des demandes de liaison.</span><span class="sxs-lookup"><span data-stu-id="587a5-110">The <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, and <xref:System.Security.CodeAccessPermission.PermitOnly%2A> stack walk modifiers do not affect the evaluation of link demands.</span></span>  <span data-ttu-id="587a5-111">Étant donné que les demandes de liaison n'effectuent pas de parcours de pile, les modificateurs de parcours de pile n'ont aucun effet sur les demandes de liaison.</span><span class="sxs-lookup"><span data-stu-id="587a5-111">Because link demands do not perform a stack walk, the stack walk modifiers have no effect on link demands.</span></span>  
  
 <span data-ttu-id="587a5-112">Si une méthode protégée par une demande de liaison est accessible via [réflexion](../../../docs/framework/reflection-and-codedom/reflection.md), puis une demande de liaison vérifie l’appelant immédiat du code accédé par réflexion.</span><span class="sxs-lookup"><span data-stu-id="587a5-112">If a method protected by a link demand is accessed through [Reflection](../../../docs/framework/reflection-and-codedom/reflection.md), then a link demand checks the immediate caller of the code accessed through reflection.</span></span> <span data-ttu-id="587a5-113">Cela est vrai à la fois pour les détections de méthodes et les appels de méthodes effectués à l'aide de la réflexion.</span><span class="sxs-lookup"><span data-stu-id="587a5-113">This is true both for method discovery and for method invocation performed using reflection.</span></span> <span data-ttu-id="587a5-114">Supposons par exemple, le code utilise la réflexion pour retourner un <xref:System.Reflection.MethodInfo> représentant une méthode protégée par une demande de liaison, puis qu’il passe de l’objet **MethodInfo** objet à un autre code qui utilise l’objet pour appeler la méthode d’origine.</span><span class="sxs-lookup"><span data-stu-id="587a5-114">For example, suppose code uses reflection to return a <xref:System.Reflection.MethodInfo> object representing a method protected by a link demand and then passes that **MethodInfo** object to some other code that uses the object to invoke the original method.</span></span> <span data-ttu-id="587a5-115">Dans ce cas, la vérification de la demande de liaison survient deux fois : une fois pour le code qui retourne la **MethodInfo** objet et une fois pour le code qui l’appelle.</span><span class="sxs-lookup"><span data-stu-id="587a5-115">In this case the link demand check occurs twice: once for the code that returns the **MethodInfo** object and once for the code that invokes it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="587a5-116">Une demande de liaison exécutée sur un constructeur de classe statique ne protège pas le constructeur, car les constructeurs statiques sont appelés par le système, en dehors du chemin d’exécution du code de l’application.</span><span class="sxs-lookup"><span data-stu-id="587a5-116">A link demand performed on a static class constructor does not protect the constructor because static constructors are called by the system, outside the application's code execution path.</span></span> <span data-ttu-id="587a5-117">Par conséquent, quand une demande de liaison est appliquée à une classe entière, elle ne peut pas protéger l'accès à un constructeur statique, même si elle protège le reste de la classe.</span><span class="sxs-lookup"><span data-stu-id="587a5-117">As a result, when a link demand is applied to an entire class, it cannot protect access to a static constructor, although it does protect the rest of the class.</span></span>  
  
 <span data-ttu-id="587a5-118">Le fragment de code suivant spécifie de manière déclarative que tout code lié à la méthode `ReadData` doit avoir l'autorisation `CustomPermission`.</span><span class="sxs-lookup"><span data-stu-id="587a5-118">The following code fragment declaratively specifies that any code linking to the `ReadData` method must have the `CustomPermission` permission.</span></span> <span data-ttu-id="587a5-119">Cette autorisation est une autorisation personnalisée hypothétique et n'existe pas dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="587a5-119">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="587a5-120">La demande est faite en passant un **SecurityAction.LinkDemand** indicateur sur le `CustomPermissionAttribute`.</span><span class="sxs-lookup"><span data-stu-id="587a5-120">The demand is made by passing a **SecurityAction.LinkDemand** flag to the `CustomPermissionAttribute`.</span></span>  
  
```vb  
<CustomPermissionAttribute(SecurityAction.LinkDemand)> _  
Public Shared Function ReadData() As String  
    ' Access a custom resource.  
End Function    
```  
  
```csharp  
[CustomPermissionAttribute(SecurityAction.LinkDemand)]  
public static string ReadData()  
{  
    // Access a custom resource.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="587a5-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="587a5-121">See Also</span></span>  
 [<span data-ttu-id="587a5-122">Attributs</span><span class="sxs-lookup"><span data-stu-id="587a5-122">Attributes</span></span>](../../../docs/standard/attributes/index.md)  
 [<span data-ttu-id="587a5-123">Sécurité d’accès du code</span><span class="sxs-lookup"><span data-stu-id="587a5-123">Code Access Security</span></span>](../../../docs/framework/misc/code-access-security.md)
