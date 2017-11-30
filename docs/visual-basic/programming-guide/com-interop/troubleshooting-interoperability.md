---
title: "Dépannage des problèmes liés à l'interopérabilité (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interop, deploying assemblies
- assemblies [Visual Basic]
- interop, installing assemblies that share components
- COM objects, troubleshooting
- interop, sharing components
- troubleshooting interoperability [Visual Basic]
- interoperability, troubleshooting
- COM interop [Visual Basic], troubleshooting
- assemblies [Visual Basic], deploying
- troubleshooting Visual Basic, interoperability
- interop assemblies
- interoperability, sharing components
- shared components, using with assemblies
ms.assetid: b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 988d07fe08a6a78ae295d13f694c55a3b8f9d2e4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-interoperability-visual-basic"></a>Dépannage des problèmes liés à l'interopérabilité (Visual Basic)
Lorsque vous interagissez entre COM et le code managé de la [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], vous pouvez rencontrer un ou plusieurs des problèmes courants suivants.  
  
##  <a name="vbconinteroperabilitymarshalinganchor1"></a>Marshaling d’interopérabilité  
 Dans certains cas, vous devrez peut-être utiliser des types de données qui ne sont pas dans le cadre de la [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Assemblys d’interopérabilité gèrent la plupart du travail pour les objets COM, mais vous devrez peut-être contrôler les types de données qui sont utilisées lorsque des objets gérés sont exposées à COM. Par exemple, les structures de bibliothèques de classes doivent indiquer la `BStr` non managé de type sur les chaînes envoyées à des objets COM créés par Visual Basic 6.0 et versions antérieures. Dans ce cas, vous pouvez utiliser la <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribut pour que les types managés à exposer en tant que types non managés.  
  
##  <a name="vbconinteroperabilitymarshalinganchor2"></a>Exportation des chaînes de longueur fixe au Code non managé  
 Dans Visual Basic 6.0 et versions antérieures, les chaînes sont exportées à des objets COM en tant que séquence d’octets sans caractère null de fin. Pour la compatibilité avec d’autres langages, Visual Basic .NET inclut un caractère de fin lors de l’exportation de chaînes. La meilleure façon de résoudre cette incompatibilité consiste à exporter les chaînes qui n’ont pas le caractère de fin comme des tableaux de `Byte` ou `Char`.  
  
##  <a name="vbconinteroperabilitymarshalinganchor3"></a>Exportation de hiérarchies d’héritage  
 Hiérarchies vous pouvez aplatir lorsqu’elle est exposée en tant qu’objets COM de classe managée. Par exemple, si vous définissez une classe de base avec un membre, puis héritez de la classe de base dans une classe dérivée qui est exposée comme un objet COM, les clients qui utilisent la classe dérivée de l’objet COM ne sera pas en mesure d’utiliser les membres hérités. Les membres de classe de base est accessible à partir des objets COM uniquement en tant qu’instances d’une classe de base et uniquement si la classe de base est également créée comme un objet COM.  
  
## <a name="overloaded-methods"></a>Méthodes surchargées  
 Bien que vous puissiez créer des méthodes surchargées avec [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], elles ne sont pas prises en charge par COM. Lorsqu’une classe qui contient des méthodes surchargées est exposée comme un objet COM, les nouveaux noms de méthodes sont générés pour les méthodes surchargées.  
  
 Par exemple, considérez une classe qui a deux surcharges de la `Synch` (méthode). Lorsque la classe est exposée comme un objet COM, les nouveaux noms de méthode générée peut être `Synch` et `Synch_2`.  
  
 Le changement de nom peut provoquer deux problèmes pour les consommateurs de l’objet COM.  
  
1.  Les clients ne peuvent pas attendre les noms de méthode générée.  
  
2.  Les noms de méthode générée dans la classe exposée comme un objet COM peuvent changer lorsque de nouvelles surcharges sont ajoutés à la classe ou de sa classe de base. Cela peut entraîner des problèmes de versioning.  
  
 Pour résoudre les problèmes, attribuez un nom unique, au lieu d’utiliser la surcharge, lorsque vous développez des objets qui seront exposées en tant qu’objets COM à chaque méthode.  
  
##  <a name="vbconinteroperabilitymarshalinganchor4"></a>Utilisation d’objets COM via les assemblys d’interopérabilité  
 Vous utilisez des assemblys PIA presque comme s’ils sont des remplacements de code managé pour les objets COM qu’ils représentent. Toutefois, car elles sont des wrappers et des objets COM réels pas, il existe certaines différences entre l’utilisation d’assemblys PIA et standard. Ces différences comprennent l’exposition des classes et des types de données pour les paramètres et valeurs de retour.  
  
##  <a name="vbconinteroperabilitymarshalinganchor5"></a>Classes exposées en tant que les deux Interfaces et Classes  
 Contrairement aux classes dans les assemblys standard, les classes COM sont exposées dans les assemblys PIA comme une interface et une classe qui représente la classe COM. Nom de l’interface est identique à celui de la classe COM. Le nom de la classe d’interopérabilité est le même que celui de la classe COM d’origine, mais avec le mot « Classe » ajouté. Par exemple, supposons que vous avez un projet avec une référence à un assembly d’interopérabilité pour un objet COM. Si la classe COM est nommée `MyComClass`, IntelliSense et l’Explorateur d’objets affichent une interface nommée `MyComClass` et une classe nommée `MyComClassClass`.  
  
##  <a name="vbconinteroperabilitymarshalinganchor6"></a>Création d’Instances d’une classe .NET Framework  
 En général, vous créez une instance d’un [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] à l’aide de la classe la `New` instruction avec un nom de classe. Une classe COM représentée par un assembly d’interopérabilité est le seul cas dans lequel vous pouvez utiliser la `New` instruction avec une interface. Sauf si vous utilisez la classe COM avec une `Inherits` instruction, vous pouvez utiliser l’interface comme vous le feriez pour une classe. Le code suivant montre comment créer un `Command` objet dans un projet qui fait référence à l’objet COM de la bibliothèque Microsoft ActiveX Data Objects 2.8 :  
  
 [!code-vb[VbVbalrInterop#20](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_1.vb)]  
  
 Toutefois, si vous utilisez la classe COM comme base d’une classe dérivée, vous devez utiliser la classe d’interopérabilité qui représente la classe COM, comme dans le code suivant :  
  
 [!code-vb[VbVbalrInterop#21](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_2.vb)]  
  
> [!NOTE]
>  Assemblys d’interopérabilité implémentent implicitement des interfaces qui représentent des classes COM. Vous ne devez pas essayer d’utiliser le `Implements` génère l’instruction pour implémenter ces interfaces ou une erreur.  
  
##  <a name="vbconinteroperabilitymarshalinganchor7"></a>Types de données pour les paramètres et valeurs de retour  
 Contrairement aux membres des assemblys standards, les membres de l’assembly PIA peuvent avoir des types de données qui diffèrent de ceux utilisés dans la déclaration d’objet d’origine. Bien que les assemblys PIA convertissent implicitement les types de COM pour les types common language runtime compatibles, vous devez prêter attention aux types de données qui sont utilisés par les deux côtés pour empêcher les erreurs d’exécution. Par exemple, dans les objets COM créés dans Visual Basic 6.0 et versions antérieures, les valeurs de type `Integer` supposent la [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] type équivalent, `Short`. Il est recommandé d’utiliser l’Explorateur d’objets pour examiner les caractéristiques des membres importés avant de les utiliser.  
  
##  <a name="vbconinteroperabilitymarshalinganchor8"></a>Méthodes COM de niveau module  
 La plupart des objets COM sont utilisés par la création d’une instance d’une classe COM à l’aide du `New` (mot clé), puis à appeler les méthodes de l’objet. Une exception à cette règle implique des objets COM qui contiennent des `AppObj` ou `GlobalMultiUse` classes COM. Ces classes sont semblables aux méthodes niveau module des classes Visual Basic .NET. Visual Basic 6.0 et les versions antérieures créent implicitement des instances de ces objets pour vous la première fois que vous appelez l’une de leurs méthodes. Par exemple, dans Visual Basic 6.0, vous pouvez ajouter une référence à la bibliothèque d’objets Microsoft DAO 3.6 et appeler le `DBEngine` méthode sans d’abord créer une instance :  
  
```vb  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 Visual Basic .NET requiert toujours créer les instances des objets COM avant de pouvoir utiliser leurs méthodes. Pour utiliser ces méthodes dans Visual Basic, déclarez une variable de la classe souhaitée et utilisez le mot clé new pour assigner l’objet à la variable objet. Le `Shared` mot clé peut être utilisé lorsque vous souhaitez vous assurer que seule une instance de la classe est créée.  
  
 [!code-vb[VbVbalrInterop#23](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_3.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor9"></a>Erreurs non gérées dans les gestionnaires d’événements  
 Un problème d’interopérabilité courant concerne les erreurs dans les gestionnaires d’événements qui gèrent les événements déclenchés par des objets COM. Ces erreurs sont ignorées, sauf si vous recherchez en particulier les erreurs à l’aide de `On Error` ou `Try...Catch...Finally` instructions. Par exemple, l’exemple suivant provient d’un projet Visual Basic .NET qui fait référence à l’objet COM de la bibliothèque Microsoft ActiveX Data Objects 2.8.  
  
 [!code-vb[VbVbalrInterop#24](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_4.vb)]  
  
 Cet exemple génère une erreur comme prévu. Toutefois, si vous essayez le même exemple sans le `Try...Catch...Finally` bloc, l’erreur est ignorée comme si vous avez utilisé la `OnError Resume Next` instruction. Sans la gestion des erreurs, la division par zéro échoue sans avertissement. Étant donné que ces erreurs ne déclenchent jamais d’erreurs d’exception non gérée, il est important que vous utilisez une forme de gestion des exceptions dans les gestionnaires d’événements qui gèrent des événements à partir des objets COM.  
  
### <a name="understanding-com-interop-errors"></a>Présentation des erreurs d’interopérabilité COM  
 Sans la gestion des erreurs, les appels interop génèrent souvent des erreurs qui fournissent peu d’informations. Si possible, utilisez gestion pour fournir plus d’informations sur les problèmes lorsqu’ils se produisent structurée des erreurs. Cela peut être particulièrement utile lorsque vous déboguez des applications. Exemple :  
  
 [!code-vb[VbVbalrInterop#25](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_5.vb)]  
  
 Vous trouverez des informations telles que la description d’erreur HRESULT et la source des erreurs COM en examinant le contenu de l’objet exception.  
  
##  <a name="vbconinteroperabilitymarshalinganchor10"></a>Problèmes de contrôle ActiveX  
 La plupart des contrôles ActiveX qui fonctionnent avec Visual Basic 6.0 fonctionne avec Visual Basic .NET sans problème. Les principales exceptions sont les contrôles conteneurs, des contrôles qui contiennent visuellement d’autres contrôles. Quelques exemples d’anciens contrôles qui ne fonctionnent pas correctement avec [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] sont les suivantes :  
  
-   Contrôle Frame de Microsoft Forms 2.0  
  
-   Contrôle Up-Down, également connu sous le contrôle spin  
  
-   Contrôle Sheridan Tab  
  
 Il existe peu de solutions pour les problèmes de contrôle ActiveX non pris en charge. Vous pouvez migrer des contrôles existants à [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] si vous possédez le code source d’origine. Sinon, vous pouvez vérifier avec les éditeurs de logiciels pour la mise à jour. NET-compatible avec les versions des contrôles pour remplacer non pris en charge les contrôles ActiveX.  
  
##  <a name="vbconinteroperabilitymarshalinganchor11"></a>Passage de propriétés en lecture seule de contrôles avec ByRef  
 Visual Basic .NET génère parfois des erreurs COM par exemple, « Error 0x800A017F CTL_E_SETNOTSUPPORTED » lorsque vous transmettez `ReadOnly` propriétés de certains anciens contrôles ActiveX comme `ByRef` paramètres à d’autres procédures. Les appels de procédure similaires à partir de Visual Basic 6.0 ne génèrent pas d’erreur et les paramètres sont traités comme si vous les avez passé par valeur. Le message d’erreur Visual Basic .NET indique que vous essayez de modifier une propriété qui n’a pas de propriété `Set` procédure.  
  
 Si vous avez accès à la procédure appelée, vous pouvez éviter cette erreur à l’aide de la `ByVal` (mot clé) pour déclarer des paramètres qui acceptent les `ReadOnly` propriétés. Exemple :  
  
 [!code-vb[VbVbalrInterop#26](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_6.vb)]  
  
 Si vous n’avez pas d’accès au code source pour la procédure appelée, vous pouvez forcer la propriété soient passés par valeur en ajoutant un jeu supplémentaire de la procédure appelante entre crochets. Par exemple, dans un projet qui fait référence à l’objet COM de la bibliothèque Microsoft ActiveX Data Objects 2.8, vous pouvez utiliser :  
  
 [!code-vb[VbVbalrInterop#27](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_7.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor12"></a>Déploiement d’assemblys exposant l’interopérabilité  
 Déploiement d’assemblys qui exposent les interfaces COM présente des défis uniques. Par exemple, un problème potentiel se produit lorsque des applications distinctes référencent le même assembly COM. Cette situation est courante lorsqu’une nouvelle version d’un assembly est installée et une autre application utilise toujours l’ancienne version de l’assembly. Si vous désinstallez un assembly partageant une DLL, vous pouvez involontairement rendre non disponible aux autres assemblys.  
  
 Pour éviter ce problème, vous devez installer les assemblys partagés pour le Global Assembly Cache (GAC) et utiliser un module de fusion pour le composant. Si vous ne pouvez pas installer l’application dans le GAC, il doit être installé dans un sous-répertoire spécifique à la version du répertoire CommonFilesFolder.  
  
 Les assemblys qui ne sont pas partagés doivent se trouver côte à côte dans le répertoire avec l’application appelante.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Tlbimp.exe (importateur de bibliothèques de types)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)  
 [Tlbexp.exe (exportateur de bibliothèques de types)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [Procédure pas à pas : implémentation de l’héritage avec les objets COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [Inherits (instruction)](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [Global Assembly Cache](../../../framework/app-domains/gac.md)
