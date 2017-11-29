---
title: "Localisation d'activité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ee7bc16-e609-469a-a3e8-8062952e2676
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f7746e2ffc61db6d7863e243396f6d1bba315150
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="activity-localization"></a><span data-ttu-id="4cfc3-102">Localisation d'activité</span><span class="sxs-lookup"><span data-stu-id="4cfc3-102">Activity Localization</span></span>
<span data-ttu-id="4cfc3-103">Lorsque les applications de workflow et les composants ont la possibilité d'être localisés dans d'autres langues et cultures, les chaînes de ressource doivent être utilisées afin qu'ils puissent être localisés sans les recompiler.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-103">When workflow applications and components have the potential to be localized into other cultures and languages, resource strings should be used so that they can be localized without recompiling.</span></span>  
  
## <a name="activity-localization"></a><span data-ttu-id="4cfc3-104">Localisation d'activité</span><span class="sxs-lookup"><span data-stu-id="4cfc3-104">Activity Localization</span></span>  
 <span data-ttu-id="4cfc3-105">Comme pour les applications devant être localisées (diffusées différentes versions pour diverses langues et cultures), toutes chaînes affichées ne doivent pas être directement encodées, mais plutôt stockées dans un fichier de ressources.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-105">As with all applications that must be localized (released in different versions for different languages and cultures), any strings that are displayed to the user should not be put directly in code, but rather stored in a resource file.</span></span> <span data-ttu-id="4cfc3-106">Les chaînes peuvent ensuite être accessible via <!--zz <xref:System.Environment.GetResourceString> --> `GetResourceString`.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-106">The strings can then be accessed through <!--zz <xref:System.Environment.GetResourceString> --> `GetResourceString`.</span></span> <span data-ttu-id="4cfc3-107">Si vous développez un composant distribué dans plusieurs langues, vous souhaitez également utiliser des chaînes de ressource pour les messages de validation de l'activité, les données de suivi définies par l'utilisateur, les messages de traçage et les messages d'erreur.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-107">If you are developing a component that is distributed in several languages, you also want to use resource strings for activity validation messages, user-defined tracking data, tracing messages, and error messages as well.</span></span>  
  
 <span data-ttu-id="4cfc3-108">L'exercice suivant montre comment utiliser un fichier de ressources.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-108">The following exercise demonstrates how to use a resource file.</span></span>  
  
#### <a name="using-resource-files-for-localized-strings"></a><span data-ttu-id="4cfc3-109">Utilisation de fichiers de ressources pour les chaînes localisées</span><span class="sxs-lookup"><span data-stu-id="4cfc3-109">Using resource files for localized strings</span></span>  
  
1.  <span data-ttu-id="4cfc3-110">Dans [!INCLUDE[vs2010](../../../includes/vs2010-md.md)], avec le bouton droit de votre projet dans **l’Explorateur de solutions** et sélectionnez **ajouter...** , **Un nouvel élément...** .</span><span class="sxs-lookup"><span data-stu-id="4cfc3-110">In [!INCLUDE[vs2010](../../../includes/vs2010-md.md)], right-click your project in **Solution Explorer** and select **Add…**, **New Item…**.</span></span>  
  
2.  <span data-ttu-id="4cfc3-111">Sélectionnez **fichier de ressources** et nommez le fichier ErrorResources.resx.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-111">Select **Resources File** and name the file ErrorResources.resx.</span></span> <span data-ttu-id="4cfc3-112">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-112">Click **Add**.</span></span>  
  
3.  <span data-ttu-id="4cfc3-113">Ouvrez le fichier de ressources.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-113">Open the resource file.</span></span> <span data-ttu-id="4cfc3-114">Ajouter une nouvelle entrée avec un **nom** d’ErrorString et une **valeur** de « l’activité n’est pas valide. »</span><span class="sxs-lookup"><span data-stu-id="4cfc3-114">Add a new entry with a **Name** of ErrorString and a **Value** of "The activity is not valid."</span></span>  
  
4.  <span data-ttu-id="4cfc3-115">Ajoutez les instructions `using` suivantes à votre classe.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-115">Add the following `using` statements to your class.</span></span>  
  
    ```  
    using System.Reflection;  
    using System.Resources;  
    ```  
  
5.  <span data-ttu-id="4cfc3-116">Créez un gestionnaire de ressources dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-116">Create a resource manager in your project.</span></span>  
  
    ```  
    ResourceManager ErrorManager;  
    ...  
    ErrorManager = new ResourceManager("MyNamespace.ErrorResources", Assembly.GetExecutingAssembly());  
    ```  
  
6.  <span data-ttu-id="4cfc3-117">Obtenez la chaîne du gestionnaire de ressources où c'est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-117">Get the string from the resource manager where it is required.</span></span>  
  
    ```  
    String errorMessage = ErrorManager.GetString("ErrorString");  
    ```  
  
 <span data-ttu-id="4cfc3-118">L'exemple de code suivant montre comment utiliser des chaînes localisées dans la méthode <xref:System.Activities.Activity.CacheMetadata%2A>.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-118">The following code sample demonstrates how to utilize localized strings in the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span>  
  
```  
       protected override void CacheMetadata(CodeActivityMetadata metadata)  
        {  
           .....  
          // rest of the code elided for brevity  
           .....  
            if (this.Value != null && this.To != null)  
            {  
                if (!TypeHelper.AreTypesCompatible(this.Value.ArgumentType, this.To.ArgumentType))  
                {  
//---------------------------------------------  
// ** SR.TypeMismatchForAssign will fetch the string from the resource manager **  
//---------------------------------------------  
                    metadata.AddValidationError(SR.TypeMismatchForAssign(  
                                this.Value.ArgumentType,  
                                this.To.ArgumentType,  
                                this.DisplayName));  
                }  
            }  
        }  
```
