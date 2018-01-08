---
title: Clrver.exe (outil CLR Version)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Clrver.exe
- CLR Version tool
ms.assetid: cbc2ee86-bdc8-4a65-a8f1-ba23bce3a699
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c09604c66b4628291b8e3c444d4c47c7aec8c026
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="clrverexe-clr-version-tool"></a><span data-ttu-id="a2462-102">Clrver.exe (outil CLR Version)</span><span class="sxs-lookup"><span data-stu-id="a2462-102">Clrver.exe (CLR Version Tool)</span></span>
<span data-ttu-id="a2462-103">L'outil de version CLR (Clrver.exe) rapporte toutes les versions installées du CLR (Common Runtime Language) sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a2462-103">The CLR Version tool (Clrver.exe) reports all the installed versions of the common language runtime (CLR) on the computer.</span></span>  
  
 <span data-ttu-id="a2462-104">Cet outil est installé automatiquement avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a2462-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="a2462-105">Pour exécuter l'outil, utilisez l'invite de commandes développeur (ou l'invite de commandes Visual Studio dans Windows 7).</span><span class="sxs-lookup"><span data-stu-id="a2462-105">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="a2462-106">Pour plus d'informations, consultez [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="a2462-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="a2462-107">À l'invite de commandes, tapez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="a2462-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2462-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2462-108">Syntax</span></span>  
  
```  
clrver [option]  
```  
  
## <a name="options"></a><span data-ttu-id="a2462-109">Options</span><span class="sxs-lookup"><span data-stu-id="a2462-109">Options</span></span>  
  
|<span data-ttu-id="a2462-110">Option</span><span class="sxs-lookup"><span data-stu-id="a2462-110">Option</span></span>|<span data-ttu-id="a2462-111">Description</span><span class="sxs-lookup"><span data-stu-id="a2462-111">Description</span></span>|  
|------------|-----------------|  
|`-all`|<span data-ttu-id="a2462-112">Affiche tous les processus de l'ordinateur qui utilisent le CLR.</span><span class="sxs-lookup"><span data-stu-id="a2462-112">Displays all processes on the computer that are using the CLR.</span></span>|  
|<span data-ttu-id="a2462-113">*pid*</span><span class="sxs-lookup"><span data-stu-id="a2462-113">*pid*</span></span>|<span data-ttu-id="a2462-114">Affiche la ou les versions du CLR utilisé par le processus qui a l'ID de processus spécifié (PID).</span><span class="sxs-lookup"><span data-stu-id="a2462-114">Displays the version(s) of the CLR used by the process that has the specified process ID (PID).</span></span>|  
|`-?`|<span data-ttu-id="a2462-115">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="a2462-115">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2462-116">Notes</span><span class="sxs-lookup"><span data-stu-id="a2462-116">Remarks</span></span>  
 <span data-ttu-id="a2462-117">Si vous appelez Clrver.exe sans option, il affiche toutes les versions de CLR installées.</span><span class="sxs-lookup"><span data-stu-id="a2462-117">If you call Clrver.exe with no options, it displays all installed CLR versions.</span></span> <span data-ttu-id="a2462-118">Si vous spécifiez PID pour un autre utilisateur, vous devez disposer des autorisations d'administrateur pour obtenir les informations de version.</span><span class="sxs-lookup"><span data-stu-id="a2462-118">If you specify a PID for another user, you must have administrative permissions to obtain the version information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2462-119">Dans Windows Vista et version ultérieure, le contrôle de compte d'utilisateur détermine les privilèges d'un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a2462-119">In Windows Vista and later, User Account Control (UAC) determines the privileges of a user.</span></span> <span data-ttu-id="a2462-120">Si vous êtes membre du groupe Administrateurs intégrés, deux jetons d'accès au moment de l'exécution vous sont assignés : un jeton d'accès utilisateur standard et un jeton d'accès administrateur.</span><span class="sxs-lookup"><span data-stu-id="a2462-120">If you are a member of the Built-in Administrators group, you are assigned two run-time access tokens: a standard user access token and an administrator access token.</span></span> <span data-ttu-id="a2462-121">Par défaut, vous êtes dans le rôle d'utilisateur standard.</span><span class="sxs-lookup"><span data-stu-id="a2462-121">By default, you are in the standard user role.</span></span> <span data-ttu-id="a2462-122">Pour exécuter le code qui requiert une autorisation d'administration, vous devez d'abord élever vos privilèges d'utilisateur standard à administrateur.</span><span class="sxs-lookup"><span data-stu-id="a2462-122">To execute code that requires administrative permission, you must first elevate your privileges from standard user to administrator.</span></span> <span data-ttu-id="a2462-123">Cela peut être effectué au démarrage de l'invite de commandes en cliquant avec le bouton droit sur l'icône de l'invite de commandes et en indiquant que vous voulez l'exécuter en tant qu'administrateur.</span><span class="sxs-lookup"><span data-stu-id="a2462-123">You can do this when you start the command prompt by right-clicking the command prompt icon and indicating that you want to run as an administrator.</span></span>  
  
 <span data-ttu-id="a2462-124">La tentative afin de déterminer la version du CLR pour des processus SYSTÈME, SERVICE LOCAL et SERVICE RÉSEAU entraîne un message indiquant que le PID n'existe pas.</span><span class="sxs-lookup"><span data-stu-id="a2462-124">Attempting to determine the CLR version for SYSTEM, LOCAL SERVICE, and NETWORK SERVICE processes results in a message indicating that the PID doesn't exist.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a2462-125">Exemples</span><span class="sxs-lookup"><span data-stu-id="a2462-125">Examples</span></span>  
 <span data-ttu-id="a2462-126">La commande suivante affiche toutes les versions du CLR installée sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a2462-126">The following command displays all the versions of the CLR installed on the computer.</span></span>  
  
 `clrver`  
  
 <span data-ttu-id="a2462-127">La commande suivante affiche la version du CLR utilisée par le processus 128.</span><span class="sxs-lookup"><span data-stu-id="a2462-127">The following command displays the version of the CLR used by process 128.</span></span>  
  
 `clrver 128`  
  
 <span data-ttu-id="a2462-128">La commande suivante affiche tous les processus gérés et la version du CLR qu'ils utilisent.</span><span class="sxs-lookup"><span data-stu-id="a2462-128">The following command displays all the managed processes and the version of the CLR they are using.</span></span>  
  
 `Clrver -all`  
  
## <a name="see-also"></a><span data-ttu-id="a2462-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2462-129">See Also</span></span>  
 [<span data-ttu-id="a2462-130">Outils</span><span class="sxs-lookup"><span data-stu-id="a2462-130">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="a2462-131">Invites de commandes</span><span class="sxs-lookup"><span data-stu-id="a2462-131">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
