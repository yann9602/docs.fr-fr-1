---
title: "Proc&#233;dure pas &#224; pas&#160;: h&#233;bergement d&#39;un WPF&#160;Clock dans Win32 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interopérabilité (WPF), didacticiels"
  - "interopérabilité (WPF), Win32"
  - "code Win32, interopérabilité WPF"
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Proc&#233;dure pas &#224; pas&#160;: h&#233;bergement d&#39;un WPF&#160;Clock dans Win32
Pour placer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans des applications [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], utilisez <xref:System.Windows.Interop.HwndSource>, qui fournit le HWND comprenant votre contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Dans un premier temps, vous créez <xref:System.Windows.Interop.HwndSource>, en lui attribuant des paramètres similaires à CreateWindow.  Vous indiquez ensuite à <xref:System.Windows.Interop.HwndSource> le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que vous souhaitez y inclure.  Enfin, vous retirez HWND de <xref:System.Windows.Interop.HwndSource>.  Cette procédure pas à pas explique comment créer un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mixte dans l'application [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], qui implémente de nouveau la boîte de dialogue **Propriétés de Date et heure** du système d'exploitation.  
  
## Composants requis  
 Consultez [Interopérabilité WPF et Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).  
  
## Comment utiliser ce didacticiel  
 Ce didacticiel se concentre sur les étapes importantes de la production d'une application d'interopérabilité.  Le didacticiel est complété par un exemple, [Interopérabilité de l'horloge Win32, exemple](http://go.microsoft.com/fwlink/?LinkID=160051), mais celui\-ci représente le produit final.  Ce didacticiel décrit les étapes comme si vous commenciez à travailler sur un projet [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] existant qui vous appartient, éventuellement un projet préexistant, et que vous ajoutiez un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hébergé à votre application.  Pouvez\-vous comparer votre produit final avec [Interopérabilité de l'horloge Win32, exemple](http://go.microsoft.com/fwlink/?LinkID=160051).  
  
## Procédure pas à pas d'inclusion de Windows Presentation Foundation dans Win32 \(HwndSource\)  
 Le graphique suivant illustre le produit final visé par ce didacticiel :  
  
 ![Boîte de dialogue Propriétés de date et d'heure](../../../../docs/framework/wpf/advanced/media/interoparch06.png "InteropArch06")  
  
 Vous pouvez recréer cette boîte de dialogue en créant le projet C\+\+ [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dans [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] et en utilisant l'éditeur de boîtes de dialogue pour créer ce qui suit :  
  
 ![Boîte de dialogue Propriétés de date et d'heure](../../../../docs/framework/wpf/advanced/media/interoparch07.png "InteropArch07")  
  
 \(L'utilisation de [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] n'est pas nécessaire pour employer <xref:System.Windows.Interop.HwndSource>, pas plus qu'il n'est nécessaire d'utiliser C\+\+ pour écrire des programmes [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Toutefois, cette méthode est relativement courante à cette fin et se prête bien à une explication pas à pas du didacticiel\).  
  
 Vous devez suivre cinq sous\-étapes particulières pour placer une horloge [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans la boîte de dialogue :  
  
1.  Permettez à votre projet [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] d'appeler le code managé \(**\/clr**\) en modifiant ses paramètres dans [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].  
  
2.  Créez un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> dans une DLL distincte.  
  
3.  Placez ce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> dans un <xref:System.Windows.Interop.HwndSource>.  
  
4.  Procurez\-vous un HWND pour ce <xref:System.Windows.Controls.Page> à l'aide de la propriété <xref:System.Windows.Interop.HwndSource.Handle%2A>.  
  
5.  Utilisez [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pour déterminer où placer le HWND dans la plus grande application [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]  
  
## \/clr  
 La première étape consiste à convertir ce projet [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] non managé en un projet capable d'appeler le code managé.  Utilisez l'option du compilateur \/clr, qui sera liée aux DLL nécessaires à utiliser, et ajustez la méthode Main en vue de l'utiliser avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Pour permettre l'utilisation du code managé dans le projet C\+\+ : cliquez avec le bouton droit sur le projet win32clock, puis sélectionnez **Propriétés**.  Dans la page de propriété **Général** \(valeur par défaut\), remplacez la prise en charge de Common Language Runtime par `/clr`.  
  
 Ajoutez ensuite les références aux DLL nécessaires pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] : PresentationCore.dll, PresentationFramework.dll, System.dll, WindowsBase.dll, UIAutomationProvider.dll et UIAutomationTypes.dll.  \(Les instructions suivantes supposent que le système d'exploitation est installé sur le lecteur C:.\)  
  
1.  Cliquez avec le bouton droit sur le projet win32clock, puis sélectionnez **Références...** Procédez ensuite comme suit dans cette boîte de dialogue :  
  
2.  Cliquez avec le bouton droit sur le projet win32clock, puis sélectionnez **Références...**  
  
3.  Cliquez sur **Ajouter une nouvelle référence**, cliquez sur l'onglet Parcourir, entrez C:\\Program Files\\Reference Assemblies\\Microsoft\\Framework\\v3.0\\PresentationCore.dll, puis cliquez sur OK.  
  
4.  Répétez cette procédure pour PresentationFramework.dll : C:\\Program Files\\Reference Assemblies\\Microsoft\\Framework\\v3.0\\PresentationFramework.dll.  
  
5.  Répétez cette procédure pour WindowsBase.dll : C:\\Program Files\\Reference Assemblies\\Microsoft\\Framework\\v3.0\\WindowsBase.dll.  
  
6.  Répétez cette procédure pour UIAutomationTypes.dll : C:\\Program Files\\Reference Assemblies\\Microsoft\\Framework\\v3.0\\UIAutomationTypes.dll.  
  
7.  Répétez cette procédure pour UIAutomationProvider.dll : C:\\Program Files\\Reference Assemblies\\Microsoft\\Framework\\v3.0\\UIAutomationProvider.dll.  
  
8.  Cliquez sur **Ajouter une nouvelle référence**, sélectionnez System.dll et cliquez sur **OK**.  
  
9. Cliquez sur **OK** afin de quitter les pages de propriétés win32clock pour l'ajout de références.  
  
 Enfin, ajoutez `STAThreadAttribute` à la méthode `_tWinMain` en vue de son utilisation avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] :  
  
```  
[System::STAThreadAttribute]  
int APIENTRY _tWinMain(HINSTANCE hInstance,  
                     HINSTANCE hPrevInstance,  
                     LPTSTR    lpCmdLine,  
                     int       nCmdShow)  
```  
  
 Cet attribut indique à [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] que, lorsqu'il initialise [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)], il doit utiliser un modèle de threads cloisonné \(STA, Single\-Threaded Apartment\), qui est nécessaire pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] \(et [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]\).  
  
## Créer une page Windows Presentation Foundation  
 Vous créez ensuite une DLL qui définit un <xref:System.Windows.Controls.Page> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Il est souvent plus facile de créer le <xref:System.Windows.Controls.Page> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] comme une application autonome, et d'écrire et de déboguer ainsi la partie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Une fois terminé, vous pouvez convertir ce projet en DLL en cliquant dessus avec le bouton droit, en sélectionnant **Propriétés**, en accédant à Application et en remplaçant le type de sortie par Bibliothèque de classes Windows.  
  
 Le projet de DLL [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] peut être combiné au projet [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] \(solution comprenant deux projets\). Pour ce faire, cliquez avec le bouton droit sur la solution, puis sélectionnez **Ajouter un projet existant**.  
  
 Pour utiliser cette DLL [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à partir du projet [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], vous devez ajouter une référence :  
  
1.  Cliquez avec le bouton droit sur le projet win32clock, puis sélectionnez **Références...**  
  
2.  Cliquez sur **Ajouter une nouvelle référence**.  
  
3.  Cliquez sur l'onglet **Projets**.  Sélectionnez WPFClock, puis cliquez sur OK.  
  
4.  Cliquez sur **OK** afin de quitter les pages de propriétés win32clock pour l'ajout de références.  
  
## HwndSource  
 Vous utilisez ensuite <xref:System.Windows.Interop.HwndSource> pour donner à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> l'apparence d'un HWND.  Vous ajoutez ce bloc de code dans un fichier C\+\+ :  
  
```  
namespace ManagedCode  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Media;  
  
    HWND GetHwnd(HWND parent, int x, int y, int width, int height) {  
        HwndSource^ source = gcnew HwndSource(  
            0, // class style  
            WS_VISIBLE | WS_CHILD, // style  
            0, // exstyle  
            x, y, width, height,  
            "hi", // NAME  
            IntPtr(parent)        // parent window   
            );  
  
        UIElement^ page = gcnew WPFClock::Clock();  
        source->RootVisual = page;  
        return (HWND) source->Handle.ToPointer();  
    }  
}  
}  
```  
  
 Il s'agit d'une longue section de code qui mérite explication.  La première partie consiste en diverses clauses qui vous évitent d'avoir à qualifier complètement tous les appels :  
  
```  
namespace ManagedCode  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Media;  
```  
  
 Vous définissez ensuite une fonction qui crée le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], place un <xref:System.Windows.Interop.HwndSource> autour et renvoie le HWND.  
  
```  
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {  
```  
  
 Vous commencez par créer un <xref:System.Windows.Interop.HwndSource> dont les paramètres sont similaires à CreateWindow :  
  
```  
HwndSource^ source = gcnew HwndSource(  
    0, // class style  
    WS_VISIBLE | WS_CHILD, // style  
    0, // exstyle  
    x, y, width, height,  
    "hi", // NAME  
    IntPtr(parent) // parent window   
    );  
```  
  
 Vous créez ensuite la classe de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en appelant son constructeur :  
  
```  
UIElement^ page = gcnew WPFClock::Clock();  
```  
  
 Vous connectez alors la page à <xref:System.Windows.Interop.HwndSource> :  
  
```  
source->RootVisual = page;  
```  
  
 Enfin, sur la dernière ligne, renvoyez le HWND de <xref:System.Windows.Interop.HwndSource> :  
  
```  
return (HWND) source->Handle.ToPointer();  
```  
  
## Positionner le HWND  
 Maintenant que vous avez un HWND contenant l'horloge [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous devez placer celui\-ci dans la boîte de dialogue [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  Si vous saviez exactement où le placer, il vous suffirait de communiquer cette taille et cet emplacement à la fonction `GetHwnd` définie précédemment.  Cependant, comme vous avez utilisé un fichier de ressources pour définir la boîte de dialogue, vous n'êtes pas absolument certain du positionnement des HWND.  Vous pouvez utiliser l'éditeur de boîtes de dialogue [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] pour placer un contrôle statique [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] à l'endroit où vous souhaitez insérer l'horloge \(« Insérer l'horloge ici »\) et utiliser cette information pour positionner l'horloge [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Lorsque vous gérez WM\_INITDIALOG, vous utilisez `GetDlgItem` pour récupérer le HWND de l'espace réservé STATIC :  
  
```  
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);  
```  
  
 Vous calculez ensuite la taille et la position de cet espace réservé STATIC afin de pouvoir placer l'horloge [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à cet emplacement :  
  
 Rectangle RECT ;  
  
```  
GetWindowRect(placeholder, &rectangle);  
int width = rectangle.right - rectangle.left;  
int height = rectangle.bottom - rectangle.top;  
POINT point;  
point.x = rectangle.left;  
point.y = rectangle.top;  
result = MapWindowPoints(NULL, hDlg, &point, 1);  
```  
  
 Vous masquez ensuite l'espace réservé STATIC :  
  
```  
ShowWindow(placeholder, SW_HIDE);  
```  
  
 Et vous créez le HWND de l'horloge [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à cet emplacement :  
  
```  
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);  
```  
  
 Pour rendre le didacticiel intéressant et créer une véritable horloge [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous devrez créer un contrôle d'horloge [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à ce stade.  Cela est essentiellement possible dans les balises, avec quelques gestionnaires d'événements seulement dans le fichier code\-behind.  Dans la mesure où ce didacticiel traite de l'interopérabilité et non de la conception du contrôle, le code complet de l'horloge [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est indiqué ici sous forme de bloc de code, sans instructions de développement détaillées ni explication de chaque partie.  N'hésitez pas à vous prêter à des expérimentations avec ce code pour modifier l'apparence ou la fonctionnalité du contrôle.  
  
 Le balisage se présente comme suit :  
  
 [!code-xml[Win32Clock#AllClockXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]  
  
 Et voici le code\-behind correspondant :  
  
 [!code-csharp[Win32Clock#AllClockCS](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]  
  
 Le résultat final se présente comme suit :  
  
 ![Boîte de dialogue Propriétés de date et d'heure](../../../../docs/framework/wpf/advanced/media/interoparch08.png "InteropArch08")  
  
 Pour comparer votre résultat final au code qui a produit cette capture d'écran, consultez [Interopérabilité de l'horloge Win32, exemple](http://go.microsoft.com/fwlink/?LinkID=160051).  
  
## Voir aussi  
 <xref:System.Windows.Interop.HwndSource>   
 [Interopérabilité WPF et Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)   
 [Interopérabilité d'horloge Win32, exemple](http://go.microsoft.com/fwlink/?LinkID=160051)