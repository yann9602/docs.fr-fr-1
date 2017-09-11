---
title: "Atténuation : MemberDescriptor.Equals"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf3735f0-0dd4-4bef-b4b0-575264e10f39
caps.latest.revision: 7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4989d3c2611b500063158955f102931902e1ab32
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-memberdescriptorequals"></a><span data-ttu-id="acf8d-102">Atténuation : MemberDescriptor.Equals</span><span class="sxs-lookup"><span data-stu-id="acf8d-102">Mitigation: MemberDescriptor.Equals</span></span>
<span data-ttu-id="acf8d-103">À partir des applications qui ciblent le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], l’implémentation de la méthode <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> a changé.</span><span class="sxs-lookup"><span data-stu-id="acf8d-103">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], the implementation of the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> method has changed.</span></span> <span data-ttu-id="acf8d-104">Étant donné que les méthodes `System.ComponentModel.EventDescriptor.Equals` et `System.ComponentModel.PropertyDescriptor.Equals` héritent de l’implémentation de la classe de base, la modification affecte également ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="acf8d-104">Because the `System.ComponentModel.EventDescriptor.Equals` and  `System.ComponentModel.PropertyDescriptor.Equals` methods inherit the base class implementation, the change also affects these methods.</span></span>  
  
 <span data-ttu-id="acf8d-105">Dans les applications qui ciblent des versions du .NET Framework antérieures au [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], une partie du test d’égalité pour la méthode <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> comparait incorrectement la propriété <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> d’un objet avec la propriété <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> de l’autre.</span><span class="sxs-lookup"><span data-stu-id="acf8d-105">In apps that target versions of the .NET Framework prior to [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], a portion of the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> method's test for equality  incorrectly compared the <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> property of one object with the <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> property of the other.</span></span> <span data-ttu-id="acf8d-106">En commençant par les applications qui ciblent le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], la méthode <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> compare la propriété <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> des deux objets.</span><span class="sxs-lookup"><span data-stu-id="acf8d-106">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> method compares the <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> property of the two objects.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="acf8d-107">Impact</span><span class="sxs-lookup"><span data-stu-id="acf8d-107">Impact</span></span>  
 <span data-ttu-id="acf8d-108">Cette modification implémente correctement le test d’égalité pour les objets <xref:System.ComponentModel.MemberDescriptor?displayProperty=fullName> et doit avoir un impact minimal.</span><span class="sxs-lookup"><span data-stu-id="acf8d-108">This change correctly implements the test for equality for <xref:System.ComponentModel.MemberDescriptor?displayProperty=fullName> objects and should have minimal impact.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="acf8d-109">Atténuation</span><span class="sxs-lookup"><span data-stu-id="acf8d-109">Mitigation</span></span>  
 <span data-ttu-id="acf8d-110">Deux solutions sont disponibles si votre application cible le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ou une version ultérieure du .NET Framework, et dépend du renvoi de `false` par la méthode <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> quand des descripteurs membres sont équivalents :</span><span class="sxs-lookup"><span data-stu-id="acf8d-110">Two workarounds are available if your app targets the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or a later version of the .NET Framework and it depends on the  <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> method sometimes returning `false` when member descriptors are equivalent:</span></span>  
  
-   <span data-ttu-id="acf8d-111">Vous pouvez refuser cette modification sans modifier votre code source en ajoutant le code suivant à la section [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section de votre fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="acf8d-111">You can opt out of this change without modifying your source code by adding the following to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value = "Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true" />  
     </runtime>  
    ```  
  
-   <span data-ttu-id="acf8d-112">Vous pouvez modifier votre code source pour restaurer le comportement précédent en comparant manuellement les propriétés <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> et <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> après avoir appelé la méthode <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName>, comme dans le fragment de code suivant.</span><span class="sxs-lookup"><span data-stu-id="acf8d-112">You can modify your source code to restore the previous behavior by manually comparing the  <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> and <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> properties after calling the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> method, as the following code fragment does.</span></span>  
  
    ```csharp  
    if (memberDescriptor1.Equals(memberDescriptor2) &   
        memberDescriptor1.Description.Equals(memberDescriptor2.Category)) {  
          // Code to execute if true.  
    }  
    else {  
          // Code to execute if false.     
    }  
    ```  
  
    ```  
    If memberDescriptor1.Equals(memberDescriptor2) And   
        memberDescriptor1.Description.Equals(memberDescriptor2.Category)  
          // Code to execute if True.  
    Else  
          // Code to execute if False.     
    End If  
    ```  
  
 <span data-ttu-id="acf8d-113">Pour les applications qui ciblent [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] et versions antérieures, vous pouvez activer cette modification en ajoutant la valeur suivante à votre fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="acf8d-113">For apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier versions, you can enable this change by adding the following value to your app.config file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="acf8d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="acf8d-114">See Also</span></span>  
 <span data-ttu-id="acf8d-115">[Modifications de reciblage](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md) </span><span class="sxs-lookup"><span data-stu-id="acf8d-115">[Retargeting Changes](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md) </span></span>  
 [<span data-ttu-id="acf8d-116">Compatibilité des applications dans la version 4.6.2</span><span class="sxs-lookup"><span data-stu-id="acf8d-116">Application Compatibility in 4.6.2</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)

