---
title: "Guide pratique pour lire des paramètres d'application en Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ea6cfc529262053daf7c8111271de2c51e9cab4e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-application-settings-in-visual-basic"></a><span data-ttu-id="4a4cd-102">Guide pratique pour lire des paramètres d'application en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4a4cd-102">How to: Read Application Settings in Visual Basic</span></span>
<span data-ttu-id="4a4cd-103">Vous pouvez lire un paramètre utilisateur en accédant à la propriété du paramètre dans l’objet `My.Settings`.</span><span class="sxs-lookup"><span data-stu-id="4a4cd-103">You can read a user setting by accessing the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="4a4cd-104">L’objet `My.Settings` expose chaque paramètre en tant que propriété.</span><span class="sxs-lookup"><span data-stu-id="4a4cd-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="4a4cd-105">Le nom de la propriété est le même que le nom du paramètre et le type de la propriété est le même que le type du paramètre.</span><span class="sxs-lookup"><span data-stu-id="4a4cd-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="4a4cd-106">La **portée** du paramètre indique si la propriété est en lecture seule. La propriété d’un paramètre de portée **Application** est en lecture seule, tandis que la propriété d’un paramètre de portée **Utilisateur** est en lecture/écriture.</span><span class="sxs-lookup"><span data-stu-id="4a4cd-106">The setting's **Scope** indicates if the property is read-only; the property for an **Application** scope setting is read-only, while the property for a **User** scope setting is read-write.</span></span> <span data-ttu-id="4a4cd-107">Pour plus d’informations, consultez [My.Settings, objet](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="4a4cd-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a4cd-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="4a4cd-108">Example</span></span>  
 <span data-ttu-id="4a4cd-109">Cet exemple affiche la valeur du paramètre `Nickname`.</span><span class="sxs-lookup"><span data-stu-id="4a4cd-109">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-read-application-settings_1.vb)]  
  
 <span data-ttu-id="4a4cd-110">Pour que cet exemple fonctionne, votre application doit avoir un paramètre `Nickname` de type `String`.</span><span class="sxs-lookup"><span data-stu-id="4a4cd-110">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span> <span data-ttu-id="4a4cd-111">Pour plus d'informations, consultez [Gestion des paramètres d’une application (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="4a4cd-111">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a4cd-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a4cd-112">See Also</span></span>  
 [<span data-ttu-id="4a4cd-113">My.Settings (objet)</span><span class="sxs-lookup"><span data-stu-id="4a4cd-113">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [<span data-ttu-id="4a4cd-114">Guide pratique pour modifier les paramètres utilisateur dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4a4cd-114">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [<span data-ttu-id="4a4cd-115">Guide pratique pour rendre persistants les paramètres utilisateur dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4a4cd-115">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [<span data-ttu-id="4a4cd-116">Guide pratique pour créer des grilles de propriétés pour les paramètres utilisateur dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4a4cd-116">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [<span data-ttu-id="4a4cd-117">Gestion des paramètres d’une application (.NET)</span><span class="sxs-lookup"><span data-stu-id="4a4cd-117">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
