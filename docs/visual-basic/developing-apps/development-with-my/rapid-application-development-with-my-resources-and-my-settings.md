---
title: "Développement rapide d'application avec My.Resources et My.Settings (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7339afdc35341739b592b2a327094754031c346c
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a><span data-ttu-id="a74ce-102">Développement rapide d'application avec My.Resources et My.Settings (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a74ce-102">Rapid Application Development with My.Resources and My.Settings (Visual Basic)</span></span>
<span data-ttu-id="a74ce-103">Le `My.Resources` objet fournit l’accès aux ressources de l’application et vous permet de récupérer dynamiquement des ressources pour votre application.</span><span class="sxs-lookup"><span data-stu-id="a74ce-103">The `My.Resources` object provides access to the application's resources and allows you to dynamically retrieve resources for your application.</span></span>  
  
## <a name="retrieving-resources"></a><span data-ttu-id="a74ce-104">Récupération de ressources</span><span class="sxs-lookup"><span data-stu-id="a74ce-104">Retrieving Resources</span></span>  
 <span data-ttu-id="a74ce-105">Un nombre de ressources, telles que les fichiers audio, les icônes, les images et les chaînes peut être récupéré via la `My.Resources` objet.</span><span class="sxs-lookup"><span data-stu-id="a74ce-105">A number of resources such as audio files, icons, images, and strings can be retrieved through the `My.Resources` object.</span></span> <span data-ttu-id="a74ce-106">Par exemple, vous pouvez accéder les fichiers de ressources spécifiques à la culture de l’application.</span><span class="sxs-lookup"><span data-stu-id="a74ce-106">For example, you can access the application's culture-specific resource files.</span></span> <span data-ttu-id="a74ce-107">L’exemple suivant définit l’icône du formulaire à l’icône nommée `Form1Icon` stockées dans le fichier de ressources de l’application.</span><span class="sxs-lookup"><span data-stu-id="a74ce-107">The following example sets the icon of the form to the icon named `Form1Icon` stored in the application's resource file.</span></span>  
  
 [!code-vb[VbVbcnMy#7](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/rapid-application-development-with-my-resources-and-my-settings_1.vb)]  
  
 <span data-ttu-id="a74ce-108">Le `My.Resources` objet expose uniquement les ressources globales.</span><span class="sxs-lookup"><span data-stu-id="a74ce-108">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="a74ce-109">Il ne fournit pas d’accès aux fichiers de ressources associés aux formulaires.</span><span class="sxs-lookup"><span data-stu-id="a74ce-109">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="a74ce-110">Vous devez accéder à des ressources du formulaire à partir du formulaire.</span><span class="sxs-lookup"><span data-stu-id="a74ce-110">You must access the form resources from the form.</span></span>  
  
 <span data-ttu-id="a74ce-111">De même, le `My.Settings` objet fournit l’accès aux paramètres de l’application et vous permet de stocker et récupérer des paramètres de propriété et d’autres informations pour votre application de manière dynamique.</span><span class="sxs-lookup"><span data-stu-id="a74ce-111">Similarly, the `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="a74ce-112">Pour plus d’informations, consultez [My.Resources (objet)](../../../visual-basic/language-reference/objects/my-resources-object.md) et [My.Settings (objet)](../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="a74ce-112">For more information, see [My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md) and [My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a74ce-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a74ce-113">See Also</span></span>  
 [<span data-ttu-id="a74ce-114">My.Resources (objet)</span><span class="sxs-lookup"><span data-stu-id="a74ce-114">My.Resources Object</span></span>](../../../visual-basic/language-reference/objects/my-resources-object.md)  
 [<span data-ttu-id="a74ce-115">My.Settings (objet)</span><span class="sxs-lookup"><span data-stu-id="a74ce-115">My.Settings Object</span></span>](../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [<span data-ttu-id="a74ce-116">Accès aux paramètres d’application</span><span class="sxs-lookup"><span data-stu-id="a74ce-116">Accessing Application Settings</span></span>](../../../visual-basic/developing-apps/programming/app-settings/accessing-application-settings.md)
