---
title: "Hébergement de contenu Win32 dans WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c92e5b045b248337f1cb96c333ac38f1228dd90
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="hosting-win32-content-in-wpf"></a><span data-ttu-id="bca39-102">Hébergement de contenu Win32 dans WPF</span><span class="sxs-lookup"><span data-stu-id="bca39-102">Hosting Win32 Content in WPF</span></span>
## <a name="prerequisites"></a><span data-ttu-id="bca39-103">Prérequis</span><span class="sxs-lookup"><span data-stu-id="bca39-103">Prerequisites</span></span>  
 <span data-ttu-id="bca39-104">Consultez [WPF et Win32 interopérabilité](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="bca39-104">See [WPF and Win32 Interoperation](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).</span></span>  
  
## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a><span data-ttu-id="bca39-105">Une procédure pas à pas de Win32 à l’intérieur de Windows Presentation Framework (HwndHost)</span><span class="sxs-lookup"><span data-stu-id="bca39-105">A Walkthrough of Win32 Inside Windows Presentation Framework (HwndHost)</span></span>  
 <span data-ttu-id="bca39-106">Pour réutiliser [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] contenu à l’intérieur de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, utilisez <xref:System.Windows.Interop.HwndHost>, qui est un contrôle qui permet à HWND de ressembler à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu.</span><span class="sxs-lookup"><span data-stu-id="bca39-106">To reuse [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] content inside [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, use <xref:System.Windows.Interop.HwndHost>, which is a control that makes HWNDs look like [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span>  <span data-ttu-id="bca39-107">Comme <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> est simple à utiliser : dérivent <xref:System.Windows.Interop.HwndHost> et implémenter `BuildWindowCore` et `DestroyWindowCore` méthodes, puis instancier votre <xref:System.Windows.Interop.HwndHost> classe dérivée et le placer à l’intérieur de votre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span><span class="sxs-lookup"><span data-stu-id="bca39-107">Like <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> is straightforward to use: derive from <xref:System.Windows.Interop.HwndHost> and implement `BuildWindowCore` and `DestroyWindowCore` methods, then instantiate your <xref:System.Windows.Interop.HwndHost> derived class and place it inside your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  
  
 <span data-ttu-id="bca39-108">Si votre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] logique est déjà empaquetée comme un contrôle, puis votre `BuildWindowCore` implémentation est légèrement plus qu’un appel à `CreateWindow`.</span><span class="sxs-lookup"><span data-stu-id="bca39-108">If your [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] logic is already packaged as a control, then your `BuildWindowCore` implementation is little more than a call to `CreateWindow`.</span></span>  <span data-ttu-id="bca39-109">Par exemple, pour créer un [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] contrôle LISTBOX dans [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="bca39-109">For example, to create a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] LISTBOX control in [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:</span></span>  
  
```  
virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {  
    HWND handle = CreateWindowEx(0, L"LISTBOX",   
    L"this is a Win32 listbox",  
    WS_CHILD | WS_VISIBLE | LBS_NOTIFY  
    | WS_VSCROLL | WS_BORDER,  
    0, 0, // x, y  
    30, 70, // height, width  
    (HWND) hwndParent.Handle.ToPointer(), // parent hwnd  
    0, // hmenu  
    0, // hinstance  
    0); // lparam  
  
    return HandleRef(this, IntPtr(handle));  
}  
  
virtual void DestroyWindowCore(HandleRef hwnd) override {  
    // HwndHost will dispose the hwnd for us  
}  
```  
  
 <span data-ttu-id="bca39-110">Mais supposons que la [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] code n’est pas tout à fait si autonome ?</span><span class="sxs-lookup"><span data-stu-id="bca39-110">But suppose the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] code is not quite so self-contained?</span></span> <span data-ttu-id="bca39-111">Si, par conséquent, vous pouvez créer un [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] boîte de dialogue zone et incorporer son contenu dans une plus grande [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span><span class="sxs-lookup"><span data-stu-id="bca39-111">If so, you can create a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialog box and embed its contents into a larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  <span data-ttu-id="bca39-112">L’exemple illustre ce dans [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] et [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)], même s’il est également possible de le faire dans une autre langue ou à la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="bca39-112">The sample shows this in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] and [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)], although it is also possible to do this in a different language or at the command line.</span></span>  
  
 <span data-ttu-id="bca39-113">Démarrer une boîte de dialogue simple, qui est compilé dans un [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] projet.</span><span class="sxs-lookup"><span data-stu-id="bca39-113">Start with a simple dialog, which is compiled into a [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] project.</span></span>  
  
 <span data-ttu-id="bca39-114">Introduisez ensuite la boîte de dialogue dans la plus grande [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application :</span><span class="sxs-lookup"><span data-stu-id="bca39-114">Next, introduce the dialog into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application:</span></span>  
  
-   <span data-ttu-id="bca39-115">Compilez le [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] comme géré (`/clr`)</span><span class="sxs-lookup"><span data-stu-id="bca39-115">Compile the [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] as managed (`/clr`)</span></span>  
  
-   <span data-ttu-id="bca39-116">Activer la boîte de dialogue dans un contrôle</span><span class="sxs-lookup"><span data-stu-id="bca39-116">Turn the dialog into a control</span></span>  
  
-   <span data-ttu-id="bca39-117">Définissez la classe dérivée de <xref:System.Windows.Interop.HwndHost> avec `BuildWindowCore` et `DestroyWindowCore` méthodes</span><span class="sxs-lookup"><span data-stu-id="bca39-117">Define the derived class of <xref:System.Windows.Interop.HwndHost> with `BuildWindowCore` and `DestroyWindowCore` methods</span></span>  
  
-   <span data-ttu-id="bca39-118">Substituer `TranslateAccelerator` méthode pour gérer les clés de la boîte de dialogue</span><span class="sxs-lookup"><span data-stu-id="bca39-118">Override `TranslateAccelerator` method to handle dialog keys</span></span>  
  
-   <span data-ttu-id="bca39-119">Substituer `TabInto` pour prendre en charge la tabulation (méthode)</span><span class="sxs-lookup"><span data-stu-id="bca39-119">Override `TabInto` method to support tabbing</span></span>  
  
-   <span data-ttu-id="bca39-120">Substituer `OnMnemonic` pour prendre en charge des mnémoniques (méthode)</span><span class="sxs-lookup"><span data-stu-id="bca39-120">Override `OnMnemonic` method to support mnemonics</span></span>  
  
-   <span data-ttu-id="bca39-121">Instanciez le <xref:System.Windows.Interop.HwndHost> sous-classe et placez-la sous le bon [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] élément</span><span class="sxs-lookup"><span data-stu-id="bca39-121">Instantiate the <xref:System.Windows.Interop.HwndHost> subclass and put it under the right [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element</span></span>  
  
### <a name="turn-the-dialog-into-a-control"></a><span data-ttu-id="bca39-122">Activer la boîte de dialogue dans un contrôle</span><span class="sxs-lookup"><span data-stu-id="bca39-122">Turn the Dialog into a Control</span></span>  
 <span data-ttu-id="bca39-123">Vous pouvez activer une boîte de dialogue en un HWND en utilisant les styles WS_CHILD et DS_CONTROL enfant.</span><span class="sxs-lookup"><span data-stu-id="bca39-123">You can turn a dialog box into a child HWND using the WS_CHILD and DS_CONTROL styles.</span></span>  <span data-ttu-id="bca39-124">Aller dans le fichier de ressources (.rc) où la boîte de dialogue est défini et recherchez le début de la définition de la boîte de dialogue :</span><span class="sxs-lookup"><span data-stu-id="bca39-124">Go into the resource file (.rc) where the dialog is defined, and find the beginning of the definition of the dialog:</span></span>  
  
```  
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121  
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU  
```  
  
 <span data-ttu-id="bca39-125">Modifier la deuxième ligne :</span><span class="sxs-lookup"><span data-stu-id="bca39-125">Change the second line to:</span></span>  
  
```  
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL  
```  
  
 <span data-ttu-id="bca39-126">Cette action ne pas entièrement l’empaqueter dans un contrôle autonome ; Vous devez toujours appeler `IsDialogMessage()` donc [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] peut traiter certains messages, mais la modification du contrôle offre un moyen simple de placer ces contrôles à l’intérieur d’un autre HWND.</span><span class="sxs-lookup"><span data-stu-id="bca39-126">This action does not fully package it into a self-contained control; you still need to call `IsDialogMessage()` so [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] can process certain messages, but the control change does provide a straightforward way of putting those controls inside another HWND.</span></span>  
  
## <a name="subclass-hwndhost"></a><span data-ttu-id="bca39-127">Sous-classe HwndHost</span><span class="sxs-lookup"><span data-stu-id="bca39-127">Subclass HwndHost</span></span>  
 <span data-ttu-id="bca39-128">Importez les espaces de noms suivants :</span><span class="sxs-lookup"><span data-stu-id="bca39-128">Import the following namespaces:</span></span>  
  
```  
namespace ManagedCpp  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Input;  
    using namespace System::Windows::Media;  
    using namespace System::Runtime::InteropServices;  
```  
  
 <span data-ttu-id="bca39-129">Puis créez une classe dérivée de <xref:System.Windows.Interop.HwndHost> et remplacez le `BuildWindowCore` et `DestroyWindowCore` méthodes :</span><span class="sxs-lookup"><span data-stu-id="bca39-129">Then create a derived class of <xref:System.Windows.Interop.HwndHost> and override the `BuildWindowCore` and `DestroyWindowCore` methods:</span></span>  
  
```  
public ref class MyHwndHost : public HwndHost, IKeyboardInputSink {  
    private:  
        HWND dialog;  
  
    protected:   
        virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {  
            InitializeGlobals();   
            dialog = CreateDialog(hInstance,   
                MAKEINTRESOURCE(IDD_DIALOG1),   
                (HWND) hwndParent.Handle.ToPointer(),  
                (DLGPROC) About);   
            return HandleRef(this, IntPtr(dialog));  
        }  
  
        virtual void DestroyWindowCore(HandleRef hwnd) override {  
            // hwnd will be disposed for us  
        }  
```  
  
 <span data-ttu-id="bca39-130">Ici, vous utilisez le `CreateDialog` pour créer la boîte de dialogue qui est vraiment un contrôle.</span><span class="sxs-lookup"><span data-stu-id="bca39-130">Here you use the `CreateDialog` to create the dialog box that is really a control.</span></span>  <span data-ttu-id="bca39-131">Dans la mesure où il s’agit d’une des premières méthodes appelée à l’intérieur de la [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], vous devez également effectuer certains standard [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] l’initialisation en appelant une fonction que vous définirez ultérieurement, appelée `InitializeGlobals()`:</span><span class="sxs-lookup"><span data-stu-id="bca39-131">Since this is one of the first methods called inside the [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], you should also do some standard [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] initialization by calling a function you will define later, called `InitializeGlobals()`:</span></span>  
  
```  
bool initialized = false;  
    void InitializeGlobals() {  
        if (initialized) return;  
        initialized = true;  
  
        // TODO: Place code here.  
        MSG msg;  
        HACCEL hAccelTable;  
  
        // Initialize global strings  
        LoadString(hInstance, IDS_APP_TITLE, szTitle, MAX_LOADSTRING);  
        LoadString(hInstance, IDC_TYPICALWIN32DIALOG, szWindowClass, MAX_LOADSTRING);  
        MyRegisterClass(hInstance);  
```  
  
### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a><span data-ttu-id="bca39-132">Substituez la méthode TranslateAccelerator pour gérer les clés de la boîte de dialogue</span><span class="sxs-lookup"><span data-stu-id="bca39-132">Override TranslateAccelerator Method to Handle Dialog Keys</span></span>  
 <span data-ttu-id="bca39-133">Si vous avez exécuté cet exemple maintenant, vous obtenez un contrôle de boîte de dialogue qui affiche, mais il serait ignorent toutes du clavier du traitement qui fait une boîte de dialogue une boîte de dialogue fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="bca39-133">If you ran this sample now, you would get a dialog control that displays, but it would ignore all of the keyboard processing that makes a dialog box a functional dialog box.</span></span>  <span data-ttu-id="bca39-134">Vous devez maintenant substituer le `TranslateAccelerator` implémentation (laquelle provient de `IKeyboardInputSink`, une interface qui <xref:System.Windows.Interop.HwndHost> implémente).</span><span class="sxs-lookup"><span data-stu-id="bca39-134">You should now override the `TranslateAccelerator` implementation (which comes from `IKeyboardInputSink`, an interface that <xref:System.Windows.Interop.HwndHost> implements).</span></span>  <span data-ttu-id="bca39-135">Cette méthode est appelée lorsque l’application reçoit WM_KEYDOWN et WM_SYSKEYDOWN.</span><span class="sxs-lookup"><span data-stu-id="bca39-135">This method gets called when the application receives WM_KEYDOWN and WM_SYSKEYDOWN.</span></span>  
  
```  
#undef TranslateAccelerator  
        virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,   
            ModifierKeys modifiers) override   
        {  
            ::MSG m = ConvertMessage(msg);  
  
            // Win32's IsDialogMessage() will handle most of our tabbing, but doesn't know   
            // what to do when it reaches the last tab stop  
            if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {  
                HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);  
                HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);  
                TraversalRequest^ request = nullptr;  
  
                if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {  
                    // this code should work, but there’s a bug with interop shift-tab in current builds                      
                    request = gcnew TraversalRequest(FocusNavigationDirection::Last);  
                }  
                else if (!GetKeyState(VK_SHIFT) && GetFocus() == lastTabStop) {  
                    request = gcnew TraversalRequest(FocusNavigationDirection::Next);  
                }  
  
                if (request != nullptr)  
                    return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);  
  
            }  
  
            // Only call IsDialogMessage for keys it will do something with.  
            if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {  
                switch (m.wParam) {  
                    case VK_TAB:  
                    case VK_LEFT:  
                    case VK_UP:  
                    case VK_RIGHT:  
                    case VK_DOWN:  
                    case VK_EXECUTE:  
                    case VK_RETURN:  
                    case VK_ESCAPE:  
                    case VK_CANCEL:  
                        IsDialogMessage(dialog, &m);  
                        // IsDialogMessage should be called ProcessDialogMessage --  
                        // it processes messages without ever really telling you  
                        // if it handled a specific message or not  
                        return true;  
                }  
            }  
  
            return false; // not a key we handled  
        }  
```  
  
 <span data-ttu-id="bca39-136">Il s’agit d’une grande quantité de code en une seule pièce, et peut opter pour des explications plus détaillées.</span><span class="sxs-lookup"><span data-stu-id="bca39-136">This is a lot of code in one piece, so it could use some more detailed explanations.</span></span>  <span data-ttu-id="bca39-137">Tout d’abord, le code à l’aide de [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] et [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] macros ; vous devez prendre en compte qu’il existe déjà une macro nommée `TranslateAccelerator`, qui est défini dans winuser.h :</span><span class="sxs-lookup"><span data-stu-id="bca39-137">First, the code using [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] and [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] macros; you need to be aware that there is already a macro named `TranslateAccelerator`, which is defined in winuser.h:</span></span>  
  
```  
#define TranslateAccelerator  TranslateAcceleratorW  
```  
  
 <span data-ttu-id="bca39-138">Assurez-vous de définir un `TranslateAccelerator` (méthode) et non un `TranslateAcceleratorW` (méthode).</span><span class="sxs-lookup"><span data-stu-id="bca39-138">So make sure to define a `TranslateAccelerator` method and not a `TranslateAcceleratorW` method.</span></span>  
  
 <span data-ttu-id="bca39-139">De même, il est à la fois le winuser.h MSG non managé et managé `Microsoft::Win32::MSG` struct.</span><span class="sxs-lookup"><span data-stu-id="bca39-139">Similarly, there is both the unmanaged winuser.h MSG and the managed `Microsoft::Win32::MSG` struct.</span></span>  <span data-ttu-id="bca39-140">Vous pouvez supprimer l’ambiguïté entre les deux à l’aide de la [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] `::` opérateur.</span><span class="sxs-lookup"><span data-stu-id="bca39-140">You can disambiguate between the two using the [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] `::` operator.</span></span>  
  
```  
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,   
    ModifierKeys modifiers) override   
{  
    ::MSG m = ConvertMessage(msg);  
```  
  
 <span data-ttu-id="bca39-141">À la fois MSG possèdent les mêmes données, mais il est parfois plus facile de travailler avec la définition non managée, donc dans cet exemple, vous pouvez définir la routine de conversion évidente :</span><span class="sxs-lookup"><span data-stu-id="bca39-141">Both MSGs have the same data, but sometimes it is easier to work with the unmanaged definition, so in this sample you can define the obvious conversion routine:</span></span>  
  
```  
::MSG ConvertMessage(System::Windows::Interop::MSG% msg) {  
    ::MSG m;  
    m.hwnd = (HWND) msg.hwnd.ToPointer();  
    m.lParam = (LPARAM) msg.lParam.ToPointer();  
    m.message = msg.message;  
    m.wParam = (WPARAM) msg.wParam.ToPointer();  
  
    m.time = msg.time;  
  
    POINT pt;  
    pt.x = msg.pt_x;  
    pt.y = msg.pt_y;  
    m.pt = pt;  
  
    return m;  
}  
```  
  
 <span data-ttu-id="bca39-142">Retour au `TranslateAccelerator`.</span><span class="sxs-lookup"><span data-stu-id="bca39-142">Back to `TranslateAccelerator`.</span></span>  <span data-ttu-id="bca39-143">Le principe de base consiste à appeler la [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fonction `IsDialogMessage` pour faire autant que possible, mais `IsDialogMessage` n’a pas accès à quoi que ce soit en dehors de la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="bca39-143">The basic principle is to call the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] function `IsDialogMessage` to do as much work as possible, but `IsDialogMessage` does not have access to anything outside the dialog.</span></span> <span data-ttu-id="bca39-144">Comme onglet utilisateur autour de la boîte de dialogue, lorsque la tabulation s’exécute après le dernier contrôle dans notre boîte de dialogue, vous devez définir le focus la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] partie en appelant `IKeyboardInputSite::OnNoMoreStops`.</span><span class="sxs-lookup"><span data-stu-id="bca39-144">As a user tab around the dialog, when tabbing runs past the last control in our dialog, you need to set focus to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion by calling `IKeyboardInputSite::OnNoMoreStops`.</span></span>  
  
```  
// Win32's IsDialogMessage() will handle most of the tabbing, but doesn't know   
// what to do when it reaches the last tab stop  
if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {  
    HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);  
    HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);  
    TraversalRequest^ request = nullptr;  
  
    if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {  
        request = gcnew TraversalRequest(FocusNavigationDirection::Last);  
    }  
    else if (!GetKeyState(VK_SHIFT) && GetFocus() ==  lastTabStop) { {  
        request = gcnew TraversalRequest(FocusNavigationDirection::Next);  
    }  
  
    if (request != nullptr)  
        return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);  
}  
```  
  
 <span data-ttu-id="bca39-145">Pour finir, appelez `IsDialogMessage`.</span><span class="sxs-lookup"><span data-stu-id="bca39-145">Finally, call `IsDialogMessage`.</span></span>  <span data-ttu-id="bca39-146">Mais l’une des responsabilités d’un `TranslateAccelerator` méthode informe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] si vous avez géré ou non la séquence de touches.</span><span class="sxs-lookup"><span data-stu-id="bca39-146">But one of the responsibilities of a `TranslateAccelerator` method is telling [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] whether you handled the keystroke or not.</span></span> <span data-ttu-id="bca39-147">Si vous le gère pas, l’événement d’entrée peut « tunneler » et se propage à travers le reste de l’application.</span><span class="sxs-lookup"><span data-stu-id="bca39-147">If you did not handle it, the input event can tunnel and bubble through the rest of the application.</span></span> <span data-ttu-id="bca39-148">Ici, vous exposerez une particularité de la gestion des messages clavier et la nature de l’architecture d’entrée dans [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bca39-148">Here, you will expose a quirk of keyboard messange handling and the nature of the input architecture in [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].</span></span> <span data-ttu-id="bca39-149">Malheureusement, `IsDialogMessage` ne retourne pas de quelque manière s’il gère une séquence de touches spécifique.</span><span class="sxs-lookup"><span data-stu-id="bca39-149">Unfortunately, `IsDialogMessage` does not return in any way whether it handles a particular keystroke.</span></span>  <span data-ttu-id="bca39-150">Pire encore, il appellera `DispatchMessage()` sur les séquences de touches ne doit pas gérer !</span><span class="sxs-lookup"><span data-stu-id="bca39-150">Even worse, it will call `DispatchMessage()` on keystrokes it should not handle!</span></span>  <span data-ttu-id="bca39-151">Afin d’avoir à la rétroconception `IsDialogMessage`et l’appeler uniquement pour les clés qu’elle gérera :</span><span class="sxs-lookup"><span data-stu-id="bca39-151">So you will have to reverse-engineer `IsDialogMessage`, and only call it for the keys you know it will handle:</span></span>  
  
```  
// Only call IsDialogMessage for keys it will do something with.  
if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {  
    switch (m.wParam) {  
        case VK_TAB:  
        case VK_LEFT:  
        case VK_UP:  
        case VK_RIGHT:  
        case VK_DOWN:  
        case VK_EXECUTE:  
        case VK_RETURN:  
        case VK_ESCAPE:  
        case VK_CANCEL:  
            IsDialogMessage(dialog, &m);  
            // IsDialogMessage should be called ProcessDialogMessage --  
            // it processes messages without ever really telling you  
            // if it handled a specific message or not  
            return true;  
    }  
```  
  
### <a name="override-tabinto-method-to-support-tabbing"></a><span data-ttu-id="bca39-152">Substituer la méthode TabInto pour la prise en charge la tabulation</span><span class="sxs-lookup"><span data-stu-id="bca39-152">Override TabInto Method to Support Tabbing</span></span>  
 <span data-ttu-id="bca39-153">Maintenant que vous avez implémenté `TranslateAccelerator`, un utilisateur peut tabuler à l’intérieur de la boîte de dialogue zone tab et dans la plus grande [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span><span class="sxs-lookup"><span data-stu-id="bca39-153">Now that you have implemented `TranslateAccelerator`, a user can tab around inside the dialog box and tab out of it into the greater [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  <span data-ttu-id="bca39-154">Mais un utilisateur ne peut pas onglet dans la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="bca39-154">But a user cannot tab back into the dialog box.</span></span>  <span data-ttu-id="bca39-155">Pour résoudre ce problème, vous substituez `TabInto`:</span><span class="sxs-lookup"><span data-stu-id="bca39-155">To solve that, you override `TabInto`:</span></span>  
  
```  
public:   
    virtual bool TabInto(TraversalRequest^ request) override {  
        if (request->FocusNavigationDirection == FocusNavigationDirection::Last) {  
            HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);  
            SetFocus(lastTabStop);  
        }  
        else {  
            HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);  
            SetFocus(firstTabStop);  
        }  
        return true;  
    }  
```  
  
 <span data-ttu-id="bca39-156">Le `TraversalRequest` paramètre indique si l’action de l’onglet est un onglet ou MAJ.</span><span class="sxs-lookup"><span data-stu-id="bca39-156">The `TraversalRequest` parameter tells you whether the tab action is a tab or shift tab.</span></span>  
  
### <a name="override-onmnemonic-method-to-support-mnemonics"></a><span data-ttu-id="bca39-157">Substituer la méthode OnMnemonic pour prendre en charge les mnémoniques</span><span class="sxs-lookup"><span data-stu-id="bca39-157">Override OnMnemonic Method to Support Mnemonics</span></span>  
 <span data-ttu-id="bca39-158">Gestion du clavier est presque terminée, mais il y a un élément manquant : mnémoniques ne fonctionnent pas.</span><span class="sxs-lookup"><span data-stu-id="bca39-158">Keyboard handling is almost complete, but there is one thing missing – mnemonics do not work.</span></span>  <span data-ttu-id="bca39-159">Si un utilisateur appuie sur alt + F, le focus ne saute pas à la « prénom : « zone d’édition.</span><span class="sxs-lookup"><span data-stu-id="bca39-159">If a user presses alt-F, focus doe not jump to the "First name:" edit box.</span></span> <span data-ttu-id="bca39-160">Par conséquent, vous remplacez le `OnMnemonic` méthode :</span><span class="sxs-lookup"><span data-stu-id="bca39-160">So, you override the `OnMnemonic` method:</span></span>  
  
```  
virtual bool OnMnemonic(System::Windows::Interop::MSG% msg, ModifierKeys modifiers) override {  
    ::MSG m = ConvertMessage(msg);  
  
    // If it's one of our mnemonics, set focus to the appropriate hwnd  
    if (msg.message == WM_SYSCHAR && GetKeyState(VK_MENU /*alt*/)) {  
        int dialogitem = 9999;  
        switch (m.wParam) {  
            case 's': dialogitem = IDOK; break;  
            case 'c': dialogitem = IDCANCEL; break;  
            case 'f': dialogitem = IDC_EDIT1; break;  
            case 'l': dialogitem = IDC_EDIT2; break;  
            case 'p': dialogitem = IDC_EDIT3; break;  
            case 'a': dialogitem = IDC_EDIT4; break;  
            case 'i': dialogitem = IDC_EDIT5; break;  
            case 't': dialogitem = IDC_EDIT6; break;  
            case 'z': dialogitem = IDC_EDIT7; break;  
        }  
        if (dialogitem != 9999) {  
            HWND hwnd = GetDlgItem(dialog, dialogitem);  
            SetFocus(hwnd);  
            return true;  
        }  
    }  
    return false; // key unhandled  
};  
```  
  
 <span data-ttu-id="bca39-161">Pourquoi ne pas appeler `IsDialogMessage` ici ?</span><span class="sxs-lookup"><span data-stu-id="bca39-161">Why not call `IsDialogMessage` here?</span></span>  <span data-ttu-id="bca39-162">Vous avez le même problème comme avant, vous devez être en mesure d’informer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] si votre code a géré la séquence de touches ou non, de code et `IsDialogMessage` ne peut pas faire.</span><span class="sxs-lookup"><span data-stu-id="bca39-162">You have the same issue as before--you need to be able to inform [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code whether your code handled the keystroke or not, and `IsDialogMessage` cannot do that.</span></span>  <span data-ttu-id="bca39-163">Il existe également un second problème car `IsDialogMessage` refuse de traiter le mnémonique si le HWND ayant le focus ne se trouve pas dans la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="bca39-163">There is also a second issue, because `IsDialogMessage` refuses to process the mnemonic if the focused HWND is not inside the dialog box.</span></span>  
  
### <a name="instantiate-the-hwndhost-derived-class"></a><span data-ttu-id="bca39-164">Instancier la classe dérivée HwndHost</span><span class="sxs-lookup"><span data-stu-id="bca39-164">Instantiate the HwndHost Derived Class</span></span>  
 <span data-ttu-id="bca39-165">Pour finir, maintenant que la prise en charge des onglet et la clé est en place, vous pouvez mettre votre <xref:System.Windows.Interop.HwndHost> dans la plus grande [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span><span class="sxs-lookup"><span data-stu-id="bca39-165">Finally, now that all the key and tab support is in place, you can put your <xref:System.Windows.Interop.HwndHost> into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  <span data-ttu-id="bca39-166">Si l’application principale est écrite [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], pour le placer dans le bon endroit le plus simple consiste à laisser vide <xref:System.Windows.Controls.Border> élément sur lequel vous souhaitez placer le <xref:System.Windows.Interop.HwndHost>.</span><span class="sxs-lookup"><span data-stu-id="bca39-166">If the main application is written in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], the easiest way to put it in the right place is to leave an empty <xref:System.Windows.Controls.Border> element where you want to put the <xref:System.Windows.Interop.HwndHost>.</span></span>  <span data-ttu-id="bca39-167">Vous créez ici une <xref:System.Windows.Controls.Border> nommé `insertHwndHostHere`:</span><span class="sxs-lookup"><span data-stu-id="bca39-167">Here you create a <xref:System.Windows.Controls.Border> named `insertHwndHostHere`:</span></span>  
  
```  
<Window x:Class="WPFApplication1.Window1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    Title="Windows Presentation Framework Application"  
    Loaded="Window1_Loaded"  
    >  
    <StackPanel>  
        <Button Content="WPF button"/>  
        <Border Name="insertHwndHostHere" Height="200" Width="500"/>  
        <Button Content="WPF button"/>  
    </StackPanel>  
</Window>  
```  
  
 <span data-ttu-id="bca39-168">Ensuite, il ne reste qu’à trouver un bon emplacement dans la séquence de code pour instancier le <xref:System.Windows.Interop.HwndHost> et connectez-la à la <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="bca39-168">Then all that remains is to find a good place in code sequence to instantiate the <xref:System.Windows.Interop.HwndHost> and connect it to the <xref:System.Windows.Controls.Border>.</span></span>  <span data-ttu-id="bca39-169">Dans cet exemple, vous allez le placer dans le constructeur de la <xref:System.Windows.Window> classe dérivée :</span><span class="sxs-lookup"><span data-stu-id="bca39-169">In this example, you will put it inside the constructor for the <xref:System.Windows.Window> derived class:</span></span>  
  
```  
public partial class Window1 : Window {  
    public Window1() {  
    }  
  
    void Window1_Loaded(object sender, RoutedEventArgs e) {  
        HwndHost host = new ManagedCpp.MyHwndHost();  
        insertHwndHostHere.Child = host;  
    }  
}  
```  
  
 <span data-ttu-id="bca39-170">Qui vous permet de :</span><span class="sxs-lookup"><span data-stu-id="bca39-170">Which gives you:</span></span>  
  
 <span data-ttu-id="bca39-171">![Capture d’écran : application WPF](../../../../docs/framework/wpf/advanced/media/interoparch09.PNG "InteropArch09")</span><span class="sxs-lookup"><span data-stu-id="bca39-171">![WPF application screen shot](../../../../docs/framework/wpf/advanced/media/interoparch09.PNG "InteropArch09")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca39-172">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bca39-172">See Also</span></span>  
 [<span data-ttu-id="bca39-173">Interopérabilité WPF et Win32</span><span class="sxs-lookup"><span data-stu-id="bca39-173">WPF and Win32 Interoperation</span></span>](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)
