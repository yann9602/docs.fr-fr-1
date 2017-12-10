---
title: "Comment : appeler une fonction Windows qui possède des types non signés (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Windows functions [Visual Basic], calling
- unsigned data types [Visual Basic]
- UShort data type [Visual Basic], using
- functions [Visual Basic], calling Windows functions
- ULong data type [Visual Basic], using
- UInteger data type [Visual Basic], using
- data types [Visual Basic], using
- unsigned types [Visual Basic]
- data types [Visual Basic], unsigned
- data types [Visual Basic], numeric
- unsigned types [Visual Basic], using
ms.assetid: c2c0e712-8dc2-43b9-b4c6-345fbb02e7ce
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5b1a306ba694d4bbfc4719fc728112964b1ce40f
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a><span data-ttu-id="635ff-102">Comment : appeler une fonction Windows qui possède des types non signés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="635ff-102">How to: Call a Windows Function that Takes Unsigned Types (Visual Basic)</span></span>
<span data-ttu-id="635ff-103">Si vous consommez une classe, un module ou une structure qui possède des membres de types d’entiers non signés, vous pouvez accéder à ces membres avec [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="635ff-103">If you are consuming a class, module, or structure that has members of unsigned integer types, you can access these members with [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a><span data-ttu-id="635ff-104">Pour appeler une fonction Windows qui prend un type non signé</span><span class="sxs-lookup"><span data-stu-id="635ff-104">To call a Windows function that takes an unsigned type</span></span>  
  
1.  <span data-ttu-id="635ff-105">Utilisez un [instruction Declare](../../../visual-basic/language-reference/statements/declare-statement.md) indiquer [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bibliothèque qui conserve la fonction, ce qui est son nom dans cette bibliothèque, quelle est sa séquence d’appel et comment convertir des chaînes lors de son appel.</span><span class="sxs-lookup"><span data-stu-id="635ff-105">Use a [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) to tell [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] which library holds the function, what its name is in that library, what its calling sequence is, and how to convert strings when calling it.</span></span>  
  
2.  <span data-ttu-id="635ff-106">Dans le `Declare` instruction, utilisez `UInteger`, `ULong`, `UShort`, ou `Byte` selon le cas pour chaque paramètre avec un type non signé.</span><span class="sxs-lookup"><span data-stu-id="635ff-106">In the `Declare` statement, use `UInteger`, `ULong`, `UShort`, or `Byte` as appropriate for each parameter with an unsigned type.</span></span>  
  
3.  <span data-ttu-id="635ff-107">Consultez la documentation de la fonction Windows que vous appelez pour rechercher les noms et valeurs de constantes.</span><span class="sxs-lookup"><span data-stu-id="635ff-107">Consult the documentation for the Windows function you are calling to find the names and values of the constants it uses.</span></span> <span data-ttu-id="635ff-108">Bon nombre d'entre elles sont définies dans le fichier WinUser.h.</span><span class="sxs-lookup"><span data-stu-id="635ff-108">Many of these are defined in the WinUser.h file.</span></span>  
  
4.  <span data-ttu-id="635ff-109">Déclarez les constantes nécessaires dans votre code.</span><span class="sxs-lookup"><span data-stu-id="635ff-109">Declare the necessary constants in your code.</span></span> <span data-ttu-id="635ff-110">Nombreuses constantes Windows sont des valeurs non signées de 32 bits, et vous devez déclarer `As``UInteger`.</span><span class="sxs-lookup"><span data-stu-id="635ff-110">Many Windows constants are 32-bit unsigned values, and you should declare these `As``UInteger`.</span></span>  
  
5.  <span data-ttu-id="635ff-111">Appelez la fonction de façon normale.</span><span class="sxs-lookup"><span data-stu-id="635ff-111">Call the function in the normal way.</span></span> <span data-ttu-id="635ff-112">L’exemple suivant appelle la fonction Windows `MessageBox`, qui prend un argument d’entier non signé.</span><span class="sxs-lookup"><span data-stu-id="635ff-112">The following example calls the Windows function `MessageBox`, which takes an unsigned integer argument.</span></span>  
  
    ```  
    Public Class windowsMessage  
        Private Declare Auto Function mb Lib "user32.dll" Alias "MessageBox" (  
            ByVal hWnd As Integer,   
            ByVal lpText As String,   
            ByVal lpCaption As String,   
            ByVal uType As UInteger) As Integer  
        Private Const MB_OK As UInteger = 0  
        Private Const MB_ICONEXCLAMATION As UInteger = &H30  
        Private Const IDOK As UInteger = 1  
        Private Const IDCLOSE As UInteger = 8  
        Private Const c As UInteger = MB_OK Or MB_ICONEXCLAMATION  
        Public Function messageThroughWindows() As String  
            Dim r As Integer = mb(0, "Click OK if you see this!",   
                "Windows API call", c)  
            Dim s As String = "Windows API MessageBox returned " &  
                 CStr(r)& vbCrLf & "(IDOK = " & CStr(IDOK) &  
                 ", IDCLOSE = " & CStr(IDCLOSE) & ")"  
            Return s  
        End Function  
    End Class  
    ```  
  
     <span data-ttu-id="635ff-113">Vous pouvez tester la fonction `messageThroughWindows` avec le code suivant.</span><span class="sxs-lookup"><span data-stu-id="635ff-113">You can test the function `messageThroughWindows` with the following code.</span></span>  
  
    ```  
    Public Sub consumeWindowsMessage()  
        Dim w As New windowsMessage  
        w.messageThroughWindows()  
    End Sub  
    ```  
  
    > [!CAUTION]
    >  <span data-ttu-id="635ff-114">Le `UInteger`, `ULong`, `UShort`, et `SByte` des types de données ne sont pas dans le cadre de la [indépendance du langage et composants indépendants du langage](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), un code conforme CLS ne peut pas consommer un composant qui les utilise.</span><span class="sxs-lookup"><span data-stu-id="635ff-114">The `UInteger`, `ULong`, `UShort`, and `SByte` data types are not part of the [Language Independence and Language-Independent Components](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot consume a component that uses them.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="635ff-115">Effectue un appel au code non managé, telles que l’interface de programmation d’application Windows (API), expose votre code à des risques de sécurité potentiels.</span><span class="sxs-lookup"><span data-stu-id="635ff-115">Making a call to unmanaged code, such as the Windows application programming interface (API), exposes your code to potential security risks.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="635ff-116">Appel de l’API Windows requiert l’autorisation de code non managé, ce qui peut affecter son exécution dans les situations de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="635ff-116">Calling the Windows API requires unmanaged code permission, which might affect its execution in partial-trust situations.</span></span> <span data-ttu-id="635ff-117">Pour plus d’informations, consultez <xref:System.Security.Permissions.SecurityPermission> et [autorisations d’accès de Code](http://msdn.microsoft.com/en-us/e5ae402f-6dda-4732-bbe8-77296630f675).</span><span class="sxs-lookup"><span data-stu-id="635ff-117">For more information, see <xref:System.Security.Permissions.SecurityPermission> and [Code Access Permissions](http://msdn.microsoft.com/en-us/e5ae402f-6dda-4732-bbe8-77296630f675).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="635ff-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="635ff-118">See Also</span></span>  
 [<span data-ttu-id="635ff-119">Types de données</span><span class="sxs-lookup"><span data-stu-id="635ff-119">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="635ff-120">Integer (type de données)</span><span class="sxs-lookup"><span data-stu-id="635ff-120">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="635ff-121">UInteger (type de données)</span><span class="sxs-lookup"><span data-stu-id="635ff-121">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
 [<span data-ttu-id="635ff-122">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="635ff-122">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="635ff-123">Procédure pas à pas : appel des API Windows</span><span class="sxs-lookup"><span data-stu-id="635ff-123">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
