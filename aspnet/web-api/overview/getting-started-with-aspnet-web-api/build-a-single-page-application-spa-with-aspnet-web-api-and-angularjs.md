---
uid: web-api/overview/getting-started-with-aspnet-web-api/build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs
title: "动手实验： 生成与 ASP.NET Web API 和 Angular.js 的单页面应用程序 (SPA) |Microsoft 文档"
author: rick-anderson
description: "在传统 web 应用程序，客户端 （浏览器） 中请求页面来启动与服务器通信。 服务器然后处理该请求..."
ms.author: aspnetcontent
manager: wpickett
ms.date: 09/30/2015
ms.topic: article
ms.assetid: 719727b7-bef3-45ad-bfe9-ba5bcdb2305f
ms.technology: dotnet-webapi
ms.prod: .net-framework
msc.legacyurl: /web-api/overview/getting-started-with-aspnet-web-api/build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs
msc.type: authoredcontent
ms.openlocfilehash: 9a748628d53878be380869ac5327de0111d2284d
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2017
---
<a name="hands-on-lab-build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs"></a><span data-ttu-id="832ef-104">动手实验： 生成与 ASP.NET Web API 和 Angular.js 的单页面应用程序 (SPA)</span><span class="sxs-lookup"><span data-stu-id="832ef-104">Hands On Lab: Build a Single Page Application (SPA) with ASP.NET Web API and Angular.js</span></span>
====================
<span data-ttu-id="832ef-105">通过[Web 营地团队](https://twitter.com/webcamps)</span><span class="sxs-lookup"><span data-stu-id="832ef-105">by [Web Camps Team](https://twitter.com/webcamps)</span></span>

[<span data-ttu-id="832ef-106">下载 Web 营地培训工具包</span><span class="sxs-lookup"><span data-stu-id="832ef-106">Download Web Camps Training Kit</span></span>](http://aka.ms/webcamps-training-kit)

> <span data-ttu-id="832ef-107">在传统 web 应用程序，客户端 （浏览器） 中请求页面来启动与服务器通信。</span><span class="sxs-lookup"><span data-stu-id="832ef-107">In traditional web applications, the client (browser) initiates the communication with the server by requesting a page.</span></span> <span data-ttu-id="832ef-108">然后，在服务器处理请求，并将页面的 HTML 发送到客户端。</span><span class="sxs-lookup"><span data-stu-id="832ef-108">The server then processes the request and sends the HTML of the page to the client.</span></span> <span data-ttu-id="832ef-109">在后续交互与页 – 例如用户导航到的链接，或提交的窗体具有数据 – 新请求发送到服务器，并重新启动流： 服务器处理请求并对新的操作请求的响应中的浏览器发送一个新页ed 客户端。</span><span class="sxs-lookup"><span data-stu-id="832ef-109">In subsequent interactions with the page –e.g. the user navigates to a link or submits a form with data– a new request is sent to the server, and the flow starts again: the server processes the request and sends a new page to the browser in response to the new action requested by the client.</span></span>
> 
> <span data-ttu-id="832ef-110">在单页面应用程序 (Spa) 中整个页面已加载，在浏览器后的初始请求，但后续交互发生通过 Ajax 请求。</span><span class="sxs-lookup"><span data-stu-id="832ef-110">In Single-Page Applications (SPAs) the entire page is loaded in the browser after the initial request, but subsequent interactions take place through Ajax requests.</span></span> <span data-ttu-id="832ef-111">这意味着，在浏览器具有更新仅已更改; 此页面的部分没有无需重新加载整个页面。</span><span class="sxs-lookup"><span data-stu-id="832ef-111">This means that the browser has to update only the portion of the page that has changed; there is no need to reload the entire page.</span></span> <span data-ttu-id="832ef-112">SPA 方法可以降低应用程序以响应用户操作，以此来更流畅体验所花费的时间。</span><span class="sxs-lookup"><span data-stu-id="832ef-112">The SPA approach reduces the time taken by the application to respond to user actions, resulting in a more fluid experience.</span></span>
> 
> <span data-ttu-id="832ef-113">SPA 的体系结构涉及到一些在传统 web 应用程序中不存在的难题。</span><span class="sxs-lookup"><span data-stu-id="832ef-113">The architecture of a SPA involves certain challenges that are not present in traditional web applications.</span></span> <span data-ttu-id="832ef-114">但是，新兴技术，如 ASP.NET Web API，JavaScript 框架类似 AngularJS 和 CSS3 提供的新样式功能使其相当容易设计和构建 Spa。</span><span class="sxs-lookup"><span data-stu-id="832ef-114">However, emerging technologies like ASP.NET Web API, JavaScript frameworks like AngularJS and new styling features provided by CSS3 make it really easy to design and build SPAs.</span></span>
> 
> <span data-ttu-id="832ef-115">在此动手实验，你将利用这些技术来实现专家 Quiz，根据 SPA 概念琐事网站。</span><span class="sxs-lookup"><span data-stu-id="832ef-115">In this hand-on lab, you will take advantage of those technologies to implement Geek Quiz, a trivia website based on the SPA concept.</span></span> <span data-ttu-id="832ef-116">首先将实现与 ASP.NET Web API 公开要检索的测验问题和存储答案的所需的终结点的服务层。</span><span class="sxs-lookup"><span data-stu-id="832ef-116">You will first implement the service layer with ASP.NET Web API to expose the required endpoints to retrieve the quiz questions and store the answers.</span></span> <span data-ttu-id="832ef-117">然后，你将构建使用 AngularJS 和 CSS3 转换效果的丰富且高度可响应用户界面。</span><span class="sxs-lookup"><span data-stu-id="832ef-117">Then, you will build a rich and responsive UI using AngularJS and CSS3 transformation effects.</span></span>
> 
> <span data-ttu-id="832ef-118">在 Web 营地培训工具包中，在包括所有的示例代码和代码段[http://aka.ms/webcamps-training-kit](http://aka.ms/webcamps-training-kit)。</span><span class="sxs-lookup"><span data-stu-id="832ef-118">All sample code and snippets are included in the Web Camps Training Kit, available at [http://aka.ms/webcamps-training-kit](http://aka.ms/webcamps-training-kit).</span></span>


## <a name="overview"></a><span data-ttu-id="832ef-119">概述</span><span class="sxs-lookup"><span data-stu-id="832ef-119">Overview</span></span>

<a id="Objectives"></a>
### <a name="objectives"></a><span data-ttu-id="832ef-120">目标</span><span class="sxs-lookup"><span data-stu-id="832ef-120">Objectives</span></span>

<span data-ttu-id="832ef-121">在此动手实验中，你将了解如何：</span><span class="sxs-lookup"><span data-stu-id="832ef-121">In this hands-on lab, you will learn how to:</span></span>

- <span data-ttu-id="832ef-122">创建 ASP.NET Web API 服务，以发送和接收 JSON 数据</span><span class="sxs-lookup"><span data-stu-id="832ef-122">Create an ASP.NET Web API service to send and receive JSON data</span></span>
- <span data-ttu-id="832ef-123">创建用户界面的响应使用 AngularJS</span><span class="sxs-lookup"><span data-stu-id="832ef-123">Create a responsive UI using AngularJS</span></span>
- <span data-ttu-id="832ef-124">增强 CSS3 转换的 UI 体验</span><span class="sxs-lookup"><span data-stu-id="832ef-124">Enhance the UI experience with CSS3 transformations</span></span>

<a id="Prerequisites"></a>
### <a name="prerequisites"></a><span data-ttu-id="832ef-125">先决条件</span><span class="sxs-lookup"><span data-stu-id="832ef-125">Prerequisites</span></span>

<span data-ttu-id="832ef-126">完成本动手实验需要以下：</span><span class="sxs-lookup"><span data-stu-id="832ef-126">The following is required to complete this hands-on lab:</span></span>

- <span data-ttu-id="832ef-127">[Visual Studio Express 2013 for Web](https://www.microsoft.com/visualstudio/)或更高版本</span><span class="sxs-lookup"><span data-stu-id="832ef-127">[Visual Studio Express 2013 for Web](https://www.microsoft.com/visualstudio/) or greater</span></span>

<a id="Setup"></a>
### <a name="setup"></a><span data-ttu-id="832ef-128">安装</span><span class="sxs-lookup"><span data-stu-id="832ef-128">Setup</span></span>

<span data-ttu-id="832ef-129">若要运行本动手实验中的练习，你将需要先设置你的环境。</span><span class="sxs-lookup"><span data-stu-id="832ef-129">In order to run the exercises in this hands-on lab, you will need to set up your environment first.</span></span>

1. <span data-ttu-id="832ef-130">打开 Windows 资源管理器并浏览到本实验的**源**文件夹。</span><span class="sxs-lookup"><span data-stu-id="832ef-130">Open Windows Explorer and browse to the lab's **Source** folder.</span></span>
2. <span data-ttu-id="832ef-131">右键单击**Setup.cmd**和选择**以管理员身份运行**以启动安装过程将配置您的环境并安装本实验的 Visual Studio 代码段。</span><span class="sxs-lookup"><span data-stu-id="832ef-131">Right-click on **Setup.cmd** and select **Run as administrator** to launch the setup process that will configure your environment and install the Visual Studio code snippets for this lab.</span></span>
3. <span data-ttu-id="832ef-132">如果显示用户帐户控制对话框中，确认操作以继续。</span><span class="sxs-lookup"><span data-stu-id="832ef-132">If the User Account Control dialog box is shown, confirm the action to proceed.</span></span>

> [!NOTE]
> <span data-ttu-id="832ef-133">请确保您已在运行安装程序之前检查本实验的所有依赖项。</span><span class="sxs-lookup"><span data-stu-id="832ef-133">Make sure you have checked all the dependencies for this lab before running the setup.</span></span>


<a id="CodeSnippets"></a>
### <a name="using-the-code-snippets"></a><span data-ttu-id="832ef-134">使用代码片段</span><span class="sxs-lookup"><span data-stu-id="832ef-134">Using the Code Snippets</span></span>

<span data-ttu-id="832ef-135">在整个实验文档中，你将指示要插入代码块。</span><span class="sxs-lookup"><span data-stu-id="832ef-135">Throughout the lab document, you will be instructed to insert code blocks.</span></span> <span data-ttu-id="832ef-136">为方便起见，大多数的此代码提供作为 Visual Studio 代码段，你可以从访问在 Visual Studio 2013，为了避免必须手动添加它。</span><span class="sxs-lookup"><span data-stu-id="832ef-136">For your convenience, most of this code is provided as Visual Studio Code Snippets, which you can access from within Visual Studio 2013 to avoid having to add it manually.</span></span>

> [!NOTE]
> <span data-ttu-id="832ef-137">每个练习均附带的开始解决方案位于**开始**本练习，您可以完成相互独立地每个练习的文件夹。</span><span class="sxs-lookup"><span data-stu-id="832ef-137">Each exercise is accompanied by a starting solution located in the **Begin** folder of the exercise that allows you to follow each exercise independently of the others.</span></span> <span data-ttu-id="832ef-138">请注意在练习过程中添加的代码段缺少这些开始解决方案中，并且可能不工作，直到完成练习。</span><span class="sxs-lookup"><span data-stu-id="832ef-138">Please be aware that the code snippets that are added during an exercise are missing from these starting solutions and may not work until you have completed the exercise.</span></span> <span data-ttu-id="832ef-139">在练习的源代码，你将找到**结束**包含具有完成相应练习中的步骤得到的代码的 Visual Studio 解决方案文件夹。</span><span class="sxs-lookup"><span data-stu-id="832ef-139">Inside the source code for an exercise, you will also find an **End** folder containing a Visual Studio solution with the code that results from completing the steps in the corresponding exercise.</span></span> <span data-ttu-id="832ef-140">如果您在演练本动手实验需要其他帮助，你可以使用这些解决方案作为指南。</span><span class="sxs-lookup"><span data-stu-id="832ef-140">You can use these solutions as guidance if you need additional help as you work through this hands-on lab.</span></span>


* * *

<a id="Exercises"></a>
## <a name="exercises"></a><span data-ttu-id="832ef-141">练习</span><span class="sxs-lookup"><span data-stu-id="832ef-141">Exercises</span></span>

<span data-ttu-id="832ef-142">本动手实验包括以下练习：</span><span class="sxs-lookup"><span data-stu-id="832ef-142">This hands-on lab includes the following exercises:</span></span>

1. [<span data-ttu-id="832ef-143">创建一个 Web API</span><span class="sxs-lookup"><span data-stu-id="832ef-143">Creating a Web API</span></span>](#Exercise1)
2. [<span data-ttu-id="832ef-144">创建 SPA 接口</span><span class="sxs-lookup"><span data-stu-id="832ef-144">Creating a SPA Interface</span></span>](#Exercise2)

<span data-ttu-id="832ef-145">估计时间来完成该实验： **60 分钟**</span><span class="sxs-lookup"><span data-stu-id="832ef-145">Estimated time to complete this lab: **60 minutes**</span></span>

> [!NOTE]
> <span data-ttu-id="832ef-146">当你首次启动 Visual Studio 时，你必须选择一个预定义的设置集合。</span><span class="sxs-lookup"><span data-stu-id="832ef-146">When you first start Visual Studio, you must select one of the predefined settings collections.</span></span> <span data-ttu-id="832ef-147">每个预定义的集合用于匹配特定的开发风格和确定窗口布局、 编辑器行为、 IntelliSense 代码段和对话框选项。</span><span class="sxs-lookup"><span data-stu-id="832ef-147">Each predefined collection is designed to match a particular development style and determines window layouts, editor behavior, IntelliSense code snippets, and dialog box options.</span></span> <span data-ttu-id="832ef-148">在本实验中的过程描述完成给定的任务 Visual Studio 中使用时所需的操作**常规开发设置**集合。</span><span class="sxs-lookup"><span data-stu-id="832ef-148">The procedures in this lab describe the actions necessary to accomplish a given task in Visual Studio when using the **General Development Settings** collection.</span></span> <span data-ttu-id="832ef-149">如果您为开发环境选择不同的设置集合，则表明可能存在你应考虑到帐户的步骤中的差异。</span><span class="sxs-lookup"><span data-stu-id="832ef-149">If you choose a different settings collection for your development environment, there may be differences in the steps that you should take into account.</span></span>


<a id="Exercise1"></a>
### <a name="exercise-1-creating-a-web-api"></a><span data-ttu-id="832ef-150">练习 1： 创建 Web API</span><span class="sxs-lookup"><span data-stu-id="832ef-150">Exercise 1: Creating a Web API</span></span>

<span data-ttu-id="832ef-151">SPA 的要点之一是服务层。</span><span class="sxs-lookup"><span data-stu-id="832ef-151">One of the key parts of a SPA is the service layer.</span></span> <span data-ttu-id="832ef-152">它负责处理发送的 UI 和到该调用的响应中返回数据的 Ajax 调用。</span><span class="sxs-lookup"><span data-stu-id="832ef-152">It is responsible for processing the Ajax calls sent by the UI and returning data in response to that call.</span></span> <span data-ttu-id="832ef-153">检索的数据应以以便分析和使用的客户端计算机可读格式显示。</span><span class="sxs-lookup"><span data-stu-id="832ef-153">The data retrieved should be presented in a machine-readable format in order to be parsed and consumed by the client.</span></span>

<span data-ttu-id="832ef-154">Web API 框架是 ASP.NET 堆栈的一部分，旨在方便地实现 HTTP 服务，通常发送和接收 JSON 或 XML 格式的数据，通过 RESTful API。</span><span class="sxs-lookup"><span data-stu-id="832ef-154">The Web API framework is part of the ASP.NET Stack and is designed to make it easy to implement HTTP services, generally sending and receiving JSON- or XML-formatted data through a RESTful API.</span></span> <span data-ttu-id="832ef-155">在本练习中将创建网站以承载专家测验应用程序，然后实现后端服务来公开和保持使用 ASP.NET Web API 的测验数据。</span><span class="sxs-lookup"><span data-stu-id="832ef-155">In this exercise you will create the Web site to host the Geek Quiz application and then implement the back-end service to expose and persist the quiz data using ASP.NET Web API.</span></span>

<a id="Ex1Task1"></a>
#### <a name="task-1--creating-the-initial-project-for-geek-quiz"></a><span data-ttu-id="832ef-156">任务 1 – 为专家测验创建初始项目</span><span class="sxs-lookup"><span data-stu-id="832ef-156">Task 1 – Creating the Initial Project for Geek Quiz</span></span>

<span data-ttu-id="832ef-157">在此任务将开始创建新的 ASP.NET MVC 项目支持 ASP.NET Web API 基于**一个 ASP.NET**项目附带了 Visual Studio 的类型。</span><span class="sxs-lookup"><span data-stu-id="832ef-157">In this task you will start creating a new ASP.NET MVC project with support for ASP.NET Web API based on the **One ASP.NET** project type that comes with Visual Studio.</span></span> <span data-ttu-id="832ef-158">**一个 ASP.NET**统一所有 ASP.NET 技术和为你提供混合并将根据需要对其进行匹配的选项。</span><span class="sxs-lookup"><span data-stu-id="832ef-158">**One ASP.NET** unifies all ASP.NET technologies and gives you the option to mix and match them as desired.</span></span> <span data-ttu-id="832ef-159">然后，你将添加实体框架模型类和数据库 initializator 要插入的测验问题。</span><span class="sxs-lookup"><span data-stu-id="832ef-159">You will then add the Entity Framework's model classes and the database initializator to insert the quiz questions.</span></span>

1. <span data-ttu-id="832ef-160">打开**Visual Studio Express 2013 for Web**和选择**文件 |新建项目...**启动一个新的解决方案。</span><span class="sxs-lookup"><span data-stu-id="832ef-160">Open **Visual Studio Express 2013 for Web** and select **File | New Project...** to start a new solution.</span></span>

    <span data-ttu-id="832ef-161">![创建新的项目](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image1.png "创建新项目")</span><span class="sxs-lookup"><span data-stu-id="832ef-161">![Creating a New Project](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image1.png "Creating a New Project")</span></span>

    <span data-ttu-id="832ef-162">*创建新项目*</span><span class="sxs-lookup"><span data-stu-id="832ef-162">*Creating a New Project*</span></span>
2. <span data-ttu-id="832ef-163">在**新项目**对话框中，选择**ASP.NET Web 应用程序**下**Visual C# |Web**选项卡。请确保**.NET Framework 4.5**是选择，将其命名*GeekQuiz*，选择**位置**单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="832ef-163">In the **New Project** dialog box, select **ASP.NET Web Application** under the **Visual C# | Web** tab. Make sure **.NET Framework 4.5** is selected, name it *GeekQuiz*, choose a **Location** and click **OK**.</span></span>

    <span data-ttu-id="832ef-164">![创建新的 ASP.NET Web 应用程序项目](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image2.png "创建新的 ASP.NET Web 应用程序项目")</span><span class="sxs-lookup"><span data-stu-id="832ef-164">![Creating a new ASP.NET Web Application project](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image2.png "Creating a new ASP.NET Web Application project")</span></span>

    <span data-ttu-id="832ef-165">*创建新的 ASP.NET Web 应用程序项目*</span><span class="sxs-lookup"><span data-stu-id="832ef-165">*Creating a new ASP.NET Web Application project*</span></span>
3. <span data-ttu-id="832ef-166">在**新建 ASP.NET 项目**对话框中，选择**MVC**模板，然后选择**Web API**选项。</span><span class="sxs-lookup"><span data-stu-id="832ef-166">In the **New ASP.NET Project** dialog box, select the **MVC** template and select the **Web API** option.</span></span> <span data-ttu-id="832ef-167">此外，请确保**身份验证**选项设置为**单个用户帐户**。</span><span class="sxs-lookup"><span data-stu-id="832ef-167">Also, make sure that the **Authentication** option is set to **Individual User Accounts**.</span></span> <span data-ttu-id="832ef-168">单击“确定”  继续。</span><span class="sxs-lookup"><span data-stu-id="832ef-168">Click **OK** to continue.</span></span>

    ![使用 MVC 模板，其中包括 Web API 组件创建新项目](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image3.png)

    <span data-ttu-id="832ef-170">*使用 MVC 模板，其中包括 Web API 组件创建新项目*</span><span class="sxs-lookup"><span data-stu-id="832ef-170">*Creating a new project with the MVC template, including Web API components*</span></span>
4. <span data-ttu-id="832ef-171">在**解决方案资源管理器**，右键单击**模型**文件夹**GeekQuiz**项目，然后选择**添加 |现有项...**.</span><span class="sxs-lookup"><span data-stu-id="832ef-171">In **Solution Explorer**, right-click the **Models** folder of the **GeekQuiz** project and select **Add | Existing Item...**.</span></span>

    <span data-ttu-id="832ef-172">![添加现有项](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image4.png "添加现有项")</span><span class="sxs-lookup"><span data-stu-id="832ef-172">![Adding an existing item](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image4.png "Adding an existing item")</span></span>

    <span data-ttu-id="832ef-173">*添加现有项*</span><span class="sxs-lookup"><span data-stu-id="832ef-173">*Adding an existing item*</span></span>
5. <span data-ttu-id="832ef-174">在**添加现有项**对话框框中，导航到**源/资产/模型**文件夹，然后选择所有文件。</span><span class="sxs-lookup"><span data-stu-id="832ef-174">In the **Add Existing Item** dialog box, navigate to the **Source/Assets/Models** folder and select all the files.</span></span> <span data-ttu-id="832ef-175">单击 **“添加”**。</span><span class="sxs-lookup"><span data-stu-id="832ef-175">Click **Add**.</span></span>

    <span data-ttu-id="832ef-176">![添加模型资产](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image5.png "添加模型资产")</span><span class="sxs-lookup"><span data-stu-id="832ef-176">![Adding the model assets](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image5.png "Adding the model assets")</span></span>

    <span data-ttu-id="832ef-177">*添加模型资产*</span><span class="sxs-lookup"><span data-stu-id="832ef-177">*Adding the model assets*</span></span>

    > [!NOTE]
    > <span data-ttu-id="832ef-178">通过将添加这些文件，你要添加数据模型、 实体框架数据库上下文和专家 Quiz 应用程序的数据库初始值设定项。</span><span class="sxs-lookup"><span data-stu-id="832ef-178">By adding these files, you are adding the data model, the Entity Framework's database context and the database initializer for the Geek Quiz application.</span></span>
    > 
    > <span data-ttu-id="832ef-179">**Entity Framework (EF)**是对象关系映射器 (ORM)，可用于创建数据访问应用程序使用而不是直接使用关系存储架构编程概念应用程序模型编程。</span><span class="sxs-lookup"><span data-stu-id="832ef-179">**Entity Framework (EF)** is an object-relational mapper (ORM) that enables you to create data access applications by programming with a conceptual application model instead of programming directly using a relational storage schema.</span></span> <span data-ttu-id="832ef-180">你可以了解有关实体框架[此处](../../../entity-framework.md)。</span><span class="sxs-lookup"><span data-stu-id="832ef-180">You can learn more about Entity Framework [here](../../../entity-framework.md).</span></span>
    > 
    > <span data-ttu-id="832ef-181">下面是你刚添加的类的说明：</span><span class="sxs-lookup"><span data-stu-id="832ef-181">The following is a description of the classes you just added:</span></span>
    > 
    > - <span data-ttu-id="832ef-182">**TriviaOption:**表示与测验问题关联的单个选项</span><span class="sxs-lookup"><span data-stu-id="832ef-182">**TriviaOption:** represents a single option associated with a quiz question</span></span>
    > - <span data-ttu-id="832ef-183">**TriviaQuestion:**表示测验问题，并公开通过关联的选项**选项**属性</span><span class="sxs-lookup"><span data-stu-id="832ef-183">**TriviaQuestion:** represents a quiz question and exposes the associated options through the **Options** property</span></span>
    > - <span data-ttu-id="832ef-184">**TriviaAnswer:**表示通过对测验问题的响应中的用户选择的选项</span><span class="sxs-lookup"><span data-stu-id="832ef-184">**TriviaAnswer:** represents the option selected by the user in response to a quiz question</span></span>
    > - <span data-ttu-id="832ef-185">**TriviaContext:**表示专家 Quiz 应用程序的实体框架数据库上下文。</span><span class="sxs-lookup"><span data-stu-id="832ef-185">**TriviaContext:** represents the Entity Framework's database context of the Geek Quiz application.</span></span> <span data-ttu-id="832ef-186">此类派生自**DContext**并公开**DbSet**表示集合的上面所述的实体的属性。</span><span class="sxs-lookup"><span data-stu-id="832ef-186">This class derives from **DContext** and exposes **DbSet** properties that represent collections of the entities described above.</span></span>
    > - <span data-ttu-id="832ef-187">**TriviaDatabaseInitializer:**的实体框架初始值设定项的实现**TriviaContext**类继承自**CreateDatabaseIfNotExists**。</span><span class="sxs-lookup"><span data-stu-id="832ef-187">**TriviaDatabaseInitializer:** the implementation of the Entity Framework initializer for the **TriviaContext** class which inherits from **CreateDatabaseIfNotExists**.</span></span> <span data-ttu-id="832ef-188">此类的默认行为是创建数据库，仅当它不存在中, 插入实体指定**种子**方法。</span><span class="sxs-lookup"><span data-stu-id="832ef-188">The default behavior of this class is to create the database only if it does not exist, inserting the entities specified in the **Seed** method.</span></span>
6. <span data-ttu-id="832ef-189">打开**Global.asax.cs**文件并添加以下 using 语句。</span><span class="sxs-lookup"><span data-stu-id="832ef-189">Open the **Global.asax.cs** file and add the following using statement.</span></span>

    [!code-csharp[Main](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/samples/sample1.cs)]
7. <span data-ttu-id="832ef-190">将以下代码添加的开头**应用程序\_启动**方法以设置**TriviaDatabaseInitializer**作为数据库初始值设定项。</span><span class="sxs-lookup"><span data-stu-id="832ef-190">Add the following code at the beginning of the **Application\_Start** method to set the **TriviaDatabaseInitializer** as the database initializer.</span></span>

    [!code-csharp[Main](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/samples/sample2.cs)]
8. <span data-ttu-id="832ef-191">修改**主页**控制器限制对访问身份验证的用户。</span><span class="sxs-lookup"><span data-stu-id="832ef-191">Modify the **Home** controller to restrict access to authenticated users.</span></span> <span data-ttu-id="832ef-192">若要执行此操作，打开**HomeController.cs**文件**控制器**文件夹并添加**Authorize**属性设为**HomeController**类定义。</span><span class="sxs-lookup"><span data-stu-id="832ef-192">To do this, open the **HomeController.cs** file inside the **Controllers** folder and add the **Authorize** attribute to the **HomeController** class definition.</span></span>

    [!code-csharp[Main](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/samples/sample3.cs)]

    > [!NOTE]
    > <span data-ttu-id="832ef-193">**Authorize**筛选检查以确定用户进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="832ef-193">The **Authorize** filter checks to see if the user is authenticated.</span></span> <span data-ttu-id="832ef-194">如果用户未通过身份验证，则将返回 HTTP 状态代码 401 （未授权），而无需调用该操作。</span><span class="sxs-lookup"><span data-stu-id="832ef-194">If the user is not authenticated, it returns HTTP status code 401 (Unauthorized) without invoking the action.</span></span> <span data-ttu-id="832ef-195">你可以应用筛选器全局范围内，在控制器级别，或各个操作级别。</span><span class="sxs-lookup"><span data-stu-id="832ef-195">You can apply the filter globally, at the controller level, or at the level of individual actions.</span></span>
9. <span data-ttu-id="832ef-196">现在，您将自定义的 web 页面，并且该品牌的布局。</span><span class="sxs-lookup"><span data-stu-id="832ef-196">You will now customize the layout of the web pages and the branding.</span></span> <span data-ttu-id="832ef-197">若要执行此操作，打开 **\_Layout.cshtml**文件**视图 |共享**文件夹和更新的内容**&lt;标题&gt;**元素替换*My ASP.NET Application*与*专家测验*.</span><span class="sxs-lookup"><span data-stu-id="832ef-197">To do this, open the **\_Layout.cshtml** file inside the **Views | Shared** folder and update the content of the **&lt;title&gt;** element by replacing *My ASP.NET Application* with *Geek Quiz*.</span></span>

    [!code-cshtml[Main](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/samples/sample4.cshtml)]
10. <span data-ttu-id="832ef-198">在相同的文件中，通过删除更新的导航栏*有关*和*联系人*链接和重命名*主页*链接到*播放*。</span><span class="sxs-lookup"><span data-stu-id="832ef-198">In the same file, update the navigation bar by removing the *About* and *Contact* links and renaming the *Home* link to *Play*.</span></span> <span data-ttu-id="832ef-199">此外，重命名*应用程序名称*链接到*专家 Quiz*。</span><span class="sxs-lookup"><span data-stu-id="832ef-199">Additionally, rename the *Application name* link to *Geek Quiz*.</span></span> <span data-ttu-id="832ef-200">导航栏的 HTML 应类似下面的代码。</span><span class="sxs-lookup"><span data-stu-id="832ef-200">The HTML for the navigation bar should look like the following code.</span></span>

    [!code-cshtml[Main](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/samples/sample5.cshtml)]
11. <span data-ttu-id="832ef-201">通过替换来更新布局页的页脚*My ASP.NET Application*与*专家 Quiz*。</span><span class="sxs-lookup"><span data-stu-id="832ef-201">Update the footer of the layout page by replacing *My ASP.NET Application* with *Geek Quiz*.</span></span> <span data-ttu-id="832ef-202">若要执行此操作，将内容**&lt;页脚&gt;**元素替换为以下突出显示代码。</span><span class="sxs-lookup"><span data-stu-id="832ef-202">To do this, replace the content of the **&lt;footer&gt;** element with the following highlighted code.</span></span>

    [!code-html[Main](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/samples/sample6.html)]

<a id="Ex1Task2"></a>
#### <a name="task-2--creating-the-triviacontroller-web-api"></a><span data-ttu-id="832ef-203">任务 2 – 创建 TriviaController Web API</span><span class="sxs-lookup"><span data-stu-id="832ef-203">Task 2 – Creating the TriviaController Web API</span></span>

<span data-ttu-id="832ef-204">你可以在上一任务中，创建专家 Quiz web 应用程序的初始结构。</span><span class="sxs-lookup"><span data-stu-id="832ef-204">In the previous task, you created the initial structure of the Geek Quiz web application.</span></span> <span data-ttu-id="832ef-205">现在，你将生成一个简单的 Web API 服务，它与测验数据模型进行交互并公开以下操作：</span><span class="sxs-lookup"><span data-stu-id="832ef-205">You will now build a simple Web API service that interacts with the quiz data model and exposes the following actions:</span></span>

- <span data-ttu-id="832ef-206">**GET/api/琐事**： 从通过身份验证的用户来响应的测验列表中检索下一个问题。</span><span class="sxs-lookup"><span data-stu-id="832ef-206">**GET /api/trivia**: Retrieves the next question from the quiz list to be answered by the authenticated user.</span></span>
- <span data-ttu-id="832ef-207">**POST/api/琐事**： 存储已经过身份验证的用户指定的测验答案。</span><span class="sxs-lookup"><span data-stu-id="832ef-207">**POST /api/trivia**: Stores the quiz answer specified by the authenticated user.</span></span>

<span data-ttu-id="832ef-208">提供 Visual Studio 的 ASP.NET 基架工具将用于创建 Web API 控制器类的基线。</span><span class="sxs-lookup"><span data-stu-id="832ef-208">You will use the ASP.NET Scaffolding tools provided by Visual Studio to create the baseline for the Web API controller class.</span></span>

1. <span data-ttu-id="832ef-209">打开**WebApiConfig.cs**文件**应用\_启动**文件夹。</span><span class="sxs-lookup"><span data-stu-id="832ef-209">Open the **WebApiConfig.cs** file inside the **App\_Start** folder.</span></span> <span data-ttu-id="832ef-210">此文件定义的 Web API 服务，如如何路由映射到 Web API 控制器操作的配置。</span><span class="sxs-lookup"><span data-stu-id="832ef-210">This file defines the configuration of the Web API service, like how routes are mapped to Web API controller actions.</span></span>
2. <span data-ttu-id="832ef-211">添加以下 using 语句开头的文件。</span><span class="sxs-lookup"><span data-stu-id="832ef-211">Add the following using statement at the beginning of the file.</span></span>

    [!code-csharp[Main](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/samples/sample7.cs)]
3. <span data-ttu-id="832ef-212">添加以下突出显示的代码**注册**方法来全局配置通过 Web API 的操作方法检索到的 JSON 数据的格式化程序。</span><span class="sxs-lookup"><span data-stu-id="832ef-212">Add the following highlighted code to the **Register** method to globally configure the formatter for the JSON data retrieved by the Web API action methods.</span></span>

    [!code-csharp[Main](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/samples/sample8.cs)]

    > [!NOTE]
    > <span data-ttu-id="832ef-213">**CamelCasePropertyNamesContractResolver**会自动将转换到的属性名称*camel*大小写形式，这是 JavaScript 中的属性名称的常规约定。</span><span class="sxs-lookup"><span data-stu-id="832ef-213">The **CamelCasePropertyNamesContractResolver** automatically converts property names to *camel* case, which is the general convention for property names in JavaScript.</span></span>
4. <span data-ttu-id="832ef-214">在**解决方案资源管理器**，右键单击**控制器**文件夹**GeekQuiz**项目，然后选择**添加 |新的基架的项...**.</span><span class="sxs-lookup"><span data-stu-id="832ef-214">In **Solution Explorer**, right-click the **Controllers** folder of the **GeekQuiz** project and select **Add | New Scaffolded Item...**.</span></span>

    <span data-ttu-id="832ef-215">![创建新的基架的项](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image6.png "创建新的基架的项")</span><span class="sxs-lookup"><span data-stu-id="832ef-215">![Creating a new scaffolded item](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image6.png "Creating a new scaffolded item")</span></span>

    <span data-ttu-id="832ef-216">*创建新的基架的项*</span><span class="sxs-lookup"><span data-stu-id="832ef-216">*Creating a new scaffolded item*</span></span>
5. <span data-ttu-id="832ef-217">在**添加基架**对话框框中，请确保**常见**的左窗格中选择节点。</span><span class="sxs-lookup"><span data-stu-id="832ef-217">In the **Add Scaffold** dialog box, make sure that the **Common** node is selected in the left pane.</span></span> <span data-ttu-id="832ef-218">然后，选择**Web API 2 Controller-Empty**模板在中心窗格中单击**添加**。</span><span class="sxs-lookup"><span data-stu-id="832ef-218">Then, select the **Web API 2 Controller - Empty** template in the center pane and click **Add**.</span></span>

    <span data-ttu-id="832ef-219">![选择 Web API 2 控制器空模板](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image7.png "选择 Web API 2 控制器空模板")</span><span class="sxs-lookup"><span data-stu-id="832ef-219">![Selecting the Web API 2 Controller Empty template](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image7.png "Selecting the Web API 2 Controller Empty template")</span></span>

    <span data-ttu-id="832ef-220">*选择 Web API 2 控制器空模板*</span><span class="sxs-lookup"><span data-stu-id="832ef-220">*Selecting the Web API 2 Controller Empty template*</span></span>

    > [!NOTE]
    > <span data-ttu-id="832ef-221">**ASP.NET 基架**是用于 ASP.NET Web 应用程序的代码生成框架。</span><span class="sxs-lookup"><span data-stu-id="832ef-221">**ASP.NET Scaffolding** is a code generation framework for ASP.NET Web applications.</span></span> <span data-ttu-id="832ef-222">Visual Studio 2013 包含为 MVC 和 Web API 项目的预安装的代码生成器。</span><span class="sxs-lookup"><span data-stu-id="832ef-222">Visual Studio 2013 includes pre-installed code generators for MVC and Web API projects.</span></span> <span data-ttu-id="832ef-223">当你想要快速添加代码以减少的时间量与数据模型交互所需开发标准数据操作，应在项目中使用基架。</span><span class="sxs-lookup"><span data-stu-id="832ef-223">You should use scaffolding in your project when you want to quickly add code that interacts with data models in order to reduce the amount of time required to develop standard data operations.</span></span>
    > 
    > <span data-ttu-id="832ef-224">基架过程还可确保在项目中安装了所有必需的依赖项。</span><span class="sxs-lookup"><span data-stu-id="832ef-224">The scaffolding process also ensures that all the required dependencies are installed in the project.</span></span> <span data-ttu-id="832ef-225">例如，如果您首先一个空 ASP.NET 项目，然后使用基架添加一个 Web API 控制器，所需的 Web API NuGet 程序包和引用将自动添加到你的项目。</span><span class="sxs-lookup"><span data-stu-id="832ef-225">For example, if you start with an empty ASP.NET project and then use scaffolding to add a Web API controller, the required Web API NuGet packages and references are added to your project automatically.</span></span>
6. <span data-ttu-id="832ef-226">在**添加控制器**对话框中，键入*TriviaController*中**控制器名称**文本框中，然后单击**添加**。</span><span class="sxs-lookup"><span data-stu-id="832ef-226">In the **Add Controller** dialog box, type *TriviaController* in the **Controller name** text box and click **Add**.</span></span>

    <span data-ttu-id="832ef-227">![添加琐事控制器](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image8.png "添加琐事控制器")</span><span class="sxs-lookup"><span data-stu-id="832ef-227">![Adding the Trivia Controller](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image8.png "Adding the Trivia Controller")</span></span>

    <span data-ttu-id="832ef-228">*添加琐事控制器*</span><span class="sxs-lookup"><span data-stu-id="832ef-228">*Adding the Trivia Controller*</span></span>
7. <span data-ttu-id="832ef-229">**TriviaController.cs**文件然后添加到**控制器**文件夹**GeekQuiz**包含一个空的项目**TriviaController**类。</span><span class="sxs-lookup"><span data-stu-id="832ef-229">The **TriviaController.cs** file is then added to the **Controllers** folder of the **GeekQuiz** project, containing an empty **TriviaController** class.</span></span> <span data-ttu-id="832ef-230">添加以下 using 语句开头的文件。</span><span class="sxs-lookup"><span data-stu-id="832ef-230">Add the following using statements at the beginning of the file.</span></span>

    <span data-ttu-id="832ef-231">(代码段- *AspNetWebApiSpa-Ex1-TriviaControllerUsings*)</span><span class="sxs-lookup"><span data-stu-id="832ef-231">(Code Snippet - *AspNetWebApiSpa - Ex1 - TriviaControllerUsings*)</span></span>

    [!code-csharp[Main](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/samples/sample9.cs)]
8. <span data-ttu-id="832ef-232">将以下代码添加的开头**TriviaController**类来定义、 初始化和释放**TriviaContext**控制器中的实例。</span><span class="sxs-lookup"><span data-stu-id="832ef-232">Add the following code at the beginning of the **TriviaController** class to define, initialize and dispose the **TriviaContext** instance in the controller.</span></span>

    <span data-ttu-id="832ef-233">(代码段- *AspNetWebApiSpa-Ex1-TriviaControllerContext*)</span><span class="sxs-lookup"><span data-stu-id="832ef-233">(Code Snippet - *AspNetWebApiSpa - Ex1 - TriviaControllerContext*)</span></span>

    [!code-csharp[Main](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/samples/sample10.cs)]

    > [!NOTE]
    > <span data-ttu-id="832ef-234">**释放**方法**TriviaController**时，将调用**释放**方法**TriviaContext**实例，这可确保所有发布使用 context 对象的资源时**TriviaContext**实例已释放或垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="832ef-234">The **Dispose** method of **TriviaController** invokes the **Dispose** method of the **TriviaContext** instance, which ensures that all the resources used by the context object are released when the **TriviaContext** instance is disposed or garbage-collected.</span></span> <span data-ttu-id="832ef-235">这包括关闭所有打开的实体框架的数据库连接。</span><span class="sxs-lookup"><span data-stu-id="832ef-235">This includes closing all database connections opened by Entity Framework.</span></span>
9. <span data-ttu-id="832ef-236">在末尾添加以下帮助器方法**TriviaController**类。</span><span class="sxs-lookup"><span data-stu-id="832ef-236">Add the following helper method at the end of the **TriviaController** class.</span></span> <span data-ttu-id="832ef-237">此方法从有待回答的精选由指定的用户数据库中检索下面的测验问题。</span><span class="sxs-lookup"><span data-stu-id="832ef-237">This method retrieves the following quiz question from the database to be answered by the specified user.</span></span>

    <span data-ttu-id="832ef-238">(代码段- *AspNetWebApiSpa-Ex1-TriviaControllerNextQuestion*)</span><span class="sxs-lookup"><span data-stu-id="832ef-238">(Code Snippet - *AspNetWebApiSpa - Ex1 - TriviaControllerNextQuestion*)</span></span>

    [!code-csharp[Main](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/samples/sample11.cs)]
10. <span data-ttu-id="832ef-239">添加以下**获取**到操作方法**TriviaController**类。</span><span class="sxs-lookup"><span data-stu-id="832ef-239">Add the following **Get** action method to the **TriviaController** class.</span></span> <span data-ttu-id="832ef-240">此操作方法调用**NextQuestionAsync**在上面的步骤以检索经过身份验证的用户的下一步问题中定义的帮助器方法。</span><span class="sxs-lookup"><span data-stu-id="832ef-240">This action method calls the **NextQuestionAsync** helper method defined in the previous step to retrieve the next question for the authenticated user.</span></span>

    <span data-ttu-id="832ef-241">(代码段- *AspNetWebApiSpa-Ex1-TriviaControllerGetAction*)</span><span class="sxs-lookup"><span data-stu-id="832ef-241">(Code Snippet - *AspNetWebApiSpa - Ex1 - TriviaControllerGetAction*)</span></span>

    [!code-csharp[Main](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/samples/sample12.cs)]
11. <span data-ttu-id="832ef-242">在末尾添加以下帮助器方法**TriviaController**类。</span><span class="sxs-lookup"><span data-stu-id="832ef-242">Add the following helper method at the end of the **TriviaController** class.</span></span> <span data-ttu-id="832ef-243">此方法的数据库中存储指定的应答，并返回一个布尔值，该值指示答案正确。</span><span class="sxs-lookup"><span data-stu-id="832ef-243">This method stores the specified answer in the database and returns a Boolean value indicating whether or not the answer is correct.</span></span>

    <span data-ttu-id="832ef-244">(代码段- *AspNetWebApiSpa-Ex1-TriviaControllerStoreAsync*)</span><span class="sxs-lookup"><span data-stu-id="832ef-244">(Code Snippet - *AspNetWebApiSpa - Ex1 - TriviaControllerStoreAsync*)</span></span>

    [!code-csharp[Main](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/samples/sample13.cs)]
12. <span data-ttu-id="832ef-245">添加以下**Post**到操作方法**TriviaController**类。</span><span class="sxs-lookup"><span data-stu-id="832ef-245">Add the following **Post** action method to the **TriviaController** class.</span></span> <span data-ttu-id="832ef-246">此操作方法将关联的身份验证的用户和调用的答案**StoreAsync**帮助器方法。</span><span class="sxs-lookup"><span data-stu-id="832ef-246">This action method associates the answer to the authenticated user and calls the **StoreAsync** helper method.</span></span> <span data-ttu-id="832ef-247">然后，它将响应发送与帮助器方法返回的布尔值。</span><span class="sxs-lookup"><span data-stu-id="832ef-247">Then, it sends a response with the Boolean value returned by the helper method.</span></span>

    <span data-ttu-id="832ef-248">(代码段- *AspNetWebApiSpa-Ex1-TriviaControllerPostAction*)</span><span class="sxs-lookup"><span data-stu-id="832ef-248">(Code Snippet - *AspNetWebApiSpa - Ex1 - TriviaControllerPostAction*)</span></span>

    [!code-csharp[Main](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/samples/sample14.cs)]
13. <span data-ttu-id="832ef-249">修改要通过将添加到已经过身份验证的用户限制访问的 Web API 控制器**Authorize**属性设为**TriviaController**类定义。</span><span class="sxs-lookup"><span data-stu-id="832ef-249">Modify the Web API controller to restrict access to authenticated users by adding the **Authorize** attribute to the **TriviaController** class definition.</span></span>

    [!code-csharp[Main](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/samples/sample15.cs)]

<a id="Ex1Task3"></a>
#### <a name="task-3--running-the-solution"></a><span data-ttu-id="832ef-250">任务 3 – 运行解决方案</span><span class="sxs-lookup"><span data-stu-id="832ef-250">Task 3 – Running the Solution</span></span>

<span data-ttu-id="832ef-251">在此任务中，你将验证你在上一任务中生成的 Web API 服务按预期工作。</span><span class="sxs-lookup"><span data-stu-id="832ef-251">In this task you will verify that the Web API service you built in the previous task is working as expected.</span></span> <span data-ttu-id="832ef-252">你将使用 Internet Explorer **F12 开发人员工具**捕获网络流量，以查看全部响应从 Web API 服务。</span><span class="sxs-lookup"><span data-stu-id="832ef-252">You will use the Internet Explorer **F12 Developer Tools** to capture the network traffic and inspect the full response from the Web API service.</span></span>

> [!NOTE]
> <span data-ttu-id="832ef-253">请确保**Internet Explorer**中选择**启动**按钮位于 Visual Studio 工具栏上。</span><span class="sxs-lookup"><span data-stu-id="832ef-253">Make sure that **Internet Explorer** is selected in the **Start** button located on the Visual Studio toolbar.</span></span>
> 
> ![Internet Explorer 选项](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image9.png)


1. <span data-ttu-id="832ef-255">按**F5**运行该解决方案。</span><span class="sxs-lookup"><span data-stu-id="832ef-255">Press **F5** to run the solution.</span></span> <span data-ttu-id="832ef-256">**登录**页应出现在浏览器。</span><span class="sxs-lookup"><span data-stu-id="832ef-256">The **Log in** page should appear in the browser.</span></span>

    > [!NOTE]
    > <span data-ttu-id="832ef-257">当应用程序启动时，默认 MVC 路由触发时，它们的默认值映射到**索引**操作**HomeController**类。</span><span class="sxs-lookup"><span data-stu-id="832ef-257">When the application starts, the default MVC route is triggered, which by default is mapped to the **Index** action of the **HomeController** class.</span></span> <span data-ttu-id="832ef-258">由于**HomeController**仅限于经过身份验证的用户 (请记住修饰该类**Authorize**练习 1 中的属性) 和存在尚没有用户通过身份验证，应用程序原始请求重定向到登录页。</span><span class="sxs-lookup"><span data-stu-id="832ef-258">Since **HomeController** is restricted to authenticated users (remember that you decorated that class with the **Authorize** attribute in Exercise 1) and there is no user authenticated yet, the application redirects the original request to the log in page.</span></span>

    <span data-ttu-id="832ef-259">![运行解决方案](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image10.png "运行解决方案")</span><span class="sxs-lookup"><span data-stu-id="832ef-259">![Running the solution](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image10.png "Running the solution")</span></span>

    <span data-ttu-id="832ef-260">*运行解决方案*</span><span class="sxs-lookup"><span data-stu-id="832ef-260">*Running the solution*</span></span>
2. <span data-ttu-id="832ef-261">单击**注册**来创建新用户。</span><span class="sxs-lookup"><span data-stu-id="832ef-261">Click **Register** to create a new user.</span></span>

    <span data-ttu-id="832ef-262">![注册一个新用户](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image11.png "注册一个新用户")</span><span class="sxs-lookup"><span data-stu-id="832ef-262">![Registering a new user](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image11.png "Registering a new user")</span></span>

    <span data-ttu-id="832ef-263">*注册一个新用户*</span><span class="sxs-lookup"><span data-stu-id="832ef-263">*Registering a new user*</span></span>
3. <span data-ttu-id="832ef-264">在**注册**页上，输入**用户名**和**密码**，然后单击**注册**。</span><span class="sxs-lookup"><span data-stu-id="832ef-264">In the **Register** page, enter a **User name** and **Password**, and then click **Register**.</span></span>

    <span data-ttu-id="832ef-265">![注册页](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image12.png "注册页")</span><span class="sxs-lookup"><span data-stu-id="832ef-265">![Register page](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image12.png "Register page")</span></span>

    <span data-ttu-id="832ef-266">*注册页*</span><span class="sxs-lookup"><span data-stu-id="832ef-266">*Register page*</span></span>
4. <span data-ttu-id="832ef-267">应用程序注册新帐户和用户经过身份验证和重定向回主页。</span><span class="sxs-lookup"><span data-stu-id="832ef-267">The application registers the new account and the user is authenticated and redirected back to the home page.</span></span>

    <span data-ttu-id="832ef-268">![用户进行身份验证](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image13.png "身份验证的用户")</span><span class="sxs-lookup"><span data-stu-id="832ef-268">![User is authenticated](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image13.png "User authenticated")</span></span>

    <span data-ttu-id="832ef-269">*用户进行身份验证*</span><span class="sxs-lookup"><span data-stu-id="832ef-269">*User is authenticated*</span></span>
5. <span data-ttu-id="832ef-270">在浏览器中，按**F12**以打开**开发人员工具**面板。</span><span class="sxs-lookup"><span data-stu-id="832ef-270">In the browser, press **F12** to open the **Developer Tools** panel.</span></span> <span data-ttu-id="832ef-271">按**CTRL + 4**或单击**网络**图标，，然后单击绿色箭头按钮，以开始捕获网络流量。</span><span class="sxs-lookup"><span data-stu-id="832ef-271">Press **CTRL + 4** or click the **Network** icon, and then click the green arrow button to begin capturing network traffic.</span></span>

    <span data-ttu-id="832ef-272">![启动 Web API 网络捕获](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image14.png "启动 Web API 网络捕获")</span><span class="sxs-lookup"><span data-stu-id="832ef-272">![Initiating Web API network capture](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image14.png "Initiating Web API network capture")</span></span>

    <span data-ttu-id="832ef-273">*启动 Web API 网络捕获*</span><span class="sxs-lookup"><span data-stu-id="832ef-273">*Initiating Web API network capture*</span></span>
6. <span data-ttu-id="832ef-274">追加**api/琐事**到浏览器的地址栏中的 URL。</span><span class="sxs-lookup"><span data-stu-id="832ef-274">Append **api/trivia** to the URL in the browser's address bar.</span></span> <span data-ttu-id="832ef-275">现在将检查从响应的详细信息**获取**中的操作方法**TriviaController**。</span><span class="sxs-lookup"><span data-stu-id="832ef-275">You will now inspect the details of the response from the **Get** action method in **TriviaController**.</span></span>

    <span data-ttu-id="832ef-276">![检索通过 Web API 的下一步问题数据](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image15.png "检索下一步问题数据通过 Web API")</span><span class="sxs-lookup"><span data-stu-id="832ef-276">![Retrieving the next question data through Web API](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image15.png "Retrieving the next question data through Web API")</span></span>

    <span data-ttu-id="832ef-277">*检索下一步问题数据通过 Web API*</span><span class="sxs-lookup"><span data-stu-id="832ef-277">*Retrieving the next question data through Web API*</span></span>

    > [!NOTE]
    > <span data-ttu-id="832ef-278">下载完成后，系统将提示与下载的文件进行操作。</span><span class="sxs-lookup"><span data-stu-id="832ef-278">Once the download finishes, you will be prompted to make an action with the downloaded file.</span></span> <span data-ttu-id="832ef-279">使对话框保持打开状态，以能够查看响应内容通过开发人员工具窗口。</span><span class="sxs-lookup"><span data-stu-id="832ef-279">Leave the dialog box open in order to be able to watch the response content through the Developers Tool window.</span></span>
7. <span data-ttu-id="832ef-280">现在，你将检查响应的正文。</span><span class="sxs-lookup"><span data-stu-id="832ef-280">Now you will inspect the body of the response.</span></span> <span data-ttu-id="832ef-281">若要执行此操作，请单击**详细信息**选项卡，然后单击**响应正文**。</span><span class="sxs-lookup"><span data-stu-id="832ef-281">To do this, click the **Details** tab and then click **Response body**.</span></span> <span data-ttu-id="832ef-282">你可以检查下载的数据是具有属性的对象**选项**(这是一份**TriviaOption**对象)， **id**和**标题**对应于这样的**TriviaQuestion**类。</span><span class="sxs-lookup"><span data-stu-id="832ef-282">You can check that the downloaded data is an object with the properties **options** (which is a list of **TriviaOption** objects), **id** and **title** that correspond to the **TriviaQuestion** class.</span></span>

    <span data-ttu-id="832ef-283">![查看 Web API 响应正文](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image16.png "查看 Web API 响应正文")</span><span class="sxs-lookup"><span data-stu-id="832ef-283">![Viewing the Web API Response Body](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image16.png "Viewing the Web API Response Body")</span></span>

    <span data-ttu-id="832ef-284">*查看 Web API 响应正文*</span><span class="sxs-lookup"><span data-stu-id="832ef-284">*Viewing Web API Response Body*</span></span>
8. <span data-ttu-id="832ef-285">返回到 Visual Studio，然后按**SHIFT + F5**来停止调试。</span><span class="sxs-lookup"><span data-stu-id="832ef-285">Go back to Visual Studio and press **SHIFT + F5** to stop debugging.</span></span>

<a id="Exercise2"></a>
### <a name="exercise-2-creating-the-spa-interface"></a><span data-ttu-id="832ef-286">练习 2： 创建 SPA 接口</span><span class="sxs-lookup"><span data-stu-id="832ef-286">Exercise 2: Creating the SPA Interface</span></span>

<span data-ttu-id="832ef-287">在本练习中您将首先生成专家 Quiz 的 web 前端部分将重点放在单页面应用程序交互使用**AngularJS**。</span><span class="sxs-lookup"><span data-stu-id="832ef-287">In this exercise you will first build the web front-end portion of Geek Quiz, focusing on the Single-Page Application interaction using **AngularJS**.</span></span> <span data-ttu-id="832ef-288">然后，你将增强 CSS3 执行丰富的动画并提供视觉效果的上下文切换到下一步转换从一个问题时的用户体验。</span><span class="sxs-lookup"><span data-stu-id="832ef-288">You will then enhance the user experience with CSS3 to perform rich animations and provide a visual effect of context switching when transitioning from one question to the next.</span></span>

<a id="Ex2Task1"></a>
#### <a name="task-1--creating-the-spa-interface-using-angularjs"></a><span data-ttu-id="832ef-289">任务 1 – 创建使用 AngularJS 的 SPA 接口</span><span class="sxs-lookup"><span data-stu-id="832ef-289">Task 1 – Creating the SPA Interface Using AngularJS</span></span>

<span data-ttu-id="832ef-290">在此任务将使用**AngularJS**实现专家 Quiz 应用程序的客户端。</span><span class="sxs-lookup"><span data-stu-id="832ef-290">In this task you will use **AngularJS** to implement the client side of the Geek Quiz application.</span></span> <span data-ttu-id="832ef-291">**AngularJS**是一种开放源代码 JavaScript 框架，它增加基于浏览器的应用程序与*模型-视图-控制器*(MVC) 功能，方便了这两个开发和测试。</span><span class="sxs-lookup"><span data-stu-id="832ef-291">**AngularJS** is an open-source JavaScript framework that augments browser-based applications with *Model-View-Controller* (MVC) capability, facilitating both development and testing.</span></span>

<span data-ttu-id="832ef-292">首先，将通过从 Visual Studio 的程序包管理器控制台安装 AngularJS。</span><span class="sxs-lookup"><span data-stu-id="832ef-292">You will start by installing AngularJS from Visual Studio's Package Manager Console.</span></span> <span data-ttu-id="832ef-293">然后，你将创建要提供专家测验应用以及要呈现的测验问题和解答使用 AngularJS 模板引擎的视图的行为的控制器。</span><span class="sxs-lookup"><span data-stu-id="832ef-293">Then, you will create the controller to provide the behavior of the Geek Quiz app and the view to render the quiz questions and answers using the AngularJS template engine.</span></span>

> [!NOTE]
> <span data-ttu-id="832ef-294">有关 AngularJS 的详细信息，请参阅[ [http://angularjs.org/](http://angularjs.org/)](http://angularjs.org/)。</span><span class="sxs-lookup"><span data-stu-id="832ef-294">For more information about AngularJS, refer to [[http://angularjs.org/](http://angularjs.org/)](http://angularjs.org/).</span></span>


1. <span data-ttu-id="832ef-295">打开**Visual Studio Express 2013 for Web**并打开**GeekQuiz.sln**解决方案位于**源/Ex2-CreatingASPAInterface/开始**文件夹。</span><span class="sxs-lookup"><span data-stu-id="832ef-295">Open **Visual Studio Express 2013 for Web** and open the **GeekQuiz.sln** solution located in the **Source/Ex2-CreatingASPAInterface/Begin** folder.</span></span> <span data-ttu-id="832ef-296">或者，继续与解决方案并在上一练习中获取。</span><span class="sxs-lookup"><span data-stu-id="832ef-296">Alternatively, you can continue with the solution that you obtained in the previous exercise.</span></span>
2. <span data-ttu-id="832ef-297">打开**程序包管理器控制台**从**工具** | **库程序包管理器**。</span><span class="sxs-lookup"><span data-stu-id="832ef-297">Open the **Package Manager Console** from **Tools** | **Library Package Manager**.</span></span> <span data-ttu-id="832ef-298">键入以下命令以安装**AngularJS.Core** NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="832ef-298">Type the following command to install the **AngularJS.Core** NuGet package.</span></span>

    [!code-powershell[Main](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/samples/sample16.ps1)]
3. <span data-ttu-id="832ef-299">在**解决方案资源管理器**，右键单击**脚本**文件夹**GeekQuiz**项目，然后选择**添加 |新文件夹**。</span><span class="sxs-lookup"><span data-stu-id="832ef-299">In **Solution Explorer**, right-click the **Scripts** folder of the **GeekQuiz** project and select **Add | New Folder**.</span></span> <span data-ttu-id="832ef-300">将文件夹命名为**应用**按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="832ef-300">Name the folder **app** and press **Enter**.</span></span>
4. <span data-ttu-id="832ef-301">右键单击**应用**文件夹只需创建并选择**添加 |JavaScript 文件**。</span><span class="sxs-lookup"><span data-stu-id="832ef-301">Right-click the **app** folder you just created and select **Add | JavaScript File**.</span></span>

    ![创建新的 JavaScript 文件](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image17.png)

    <span data-ttu-id="832ef-303">*创建新的 JavaScript 文件*</span><span class="sxs-lookup"><span data-stu-id="832ef-303">*Creating a new JavaScript file*</span></span>
5. <span data-ttu-id="832ef-304">在**指定项名称**对话框中，键入*测验控制器*中**项名称**文本框中，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="832ef-304">In the **Specify Name for Item** dialog box, type *quiz-controller* in the **Item name** text box and click **OK**.</span></span>

    ![命名新的 JavaScript 文件](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image18.png)

    <span data-ttu-id="832ef-306">*命名新的 JavaScript 文件*</span><span class="sxs-lookup"><span data-stu-id="832ef-306">*Naming the new JavaScript file*</span></span>
6. <span data-ttu-id="832ef-307">在**测验 controller.js**文件中，添加以下代码以声明和初始化 AngularJS **QuizCtrl**控制器。</span><span class="sxs-lookup"><span data-stu-id="832ef-307">In the **quiz-controller.js** file, add the following code to declare and initialize the AngularJS **QuizCtrl** controller.</span></span>

    <span data-ttu-id="832ef-308">(代码段- *AspNetWebApiSpa-Ex2-AngularQuizController*)</span><span class="sxs-lookup"><span data-stu-id="832ef-308">(Code Snippet - *AspNetWebApiSpa - Ex2 - AngularQuizController*)</span></span>

    [!code-javascript[Main](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/samples/sample17.js)]

    > [!NOTE]
    > <span data-ttu-id="832ef-309">构造函数的**QuizCtrl**控制器需要名为的注射参数**$scope**。</span><span class="sxs-lookup"><span data-stu-id="832ef-309">The constructor function of the **QuizCtrl** controller expects an injectable parameter named **$scope**.</span></span> <span data-ttu-id="832ef-310">作用域的初始状态应设置在构造函数中通过附加到属性**$scope**对象。</span><span class="sxs-lookup"><span data-stu-id="832ef-310">The initial state of the scope should be set up in the constructor function by attaching properties to the **$scope** object.</span></span> <span data-ttu-id="832ef-311">属性包含**视图模型**，并可供模板时注册了该控制器。</span><span class="sxs-lookup"><span data-stu-id="832ef-311">The properties contain the **view model**, and will be accessible to the template when the controller is registered.</span></span>
    > 
    > <span data-ttu-id="832ef-312">**QuizCtrl**控制器定义在名为模块内**QuizApp**。</span><span class="sxs-lookup"><span data-stu-id="832ef-312">The **QuizCtrl** controller is defined inside a module named **QuizApp**.</span></span> <span data-ttu-id="832ef-313">模块是工作的让你单元将应用程序分解为单独的组件。</span><span class="sxs-lookup"><span data-stu-id="832ef-313">Modules are units of work that let you break your application into separate components.</span></span> <span data-ttu-id="832ef-314">使用模块的主要优势是易于理解的代码，并便于单元测试、 可重用性和可维护性。</span><span class="sxs-lookup"><span data-stu-id="832ef-314">The main advantages of using modules is that the code is easier to understand and facilitates unit testing, reusability and maintainability.</span></span>
7. <span data-ttu-id="832ef-315">若要对从视图触发的事件做出响应，现在将将行为添加到作用域。</span><span class="sxs-lookup"><span data-stu-id="832ef-315">You will now add behavior to the scope in order to react to events triggered from the view.</span></span> <span data-ttu-id="832ef-316">将以下代码添加在结束**QuizCtrl**控制器定义**nextQuestion**函数中**$scope**对象。</span><span class="sxs-lookup"><span data-stu-id="832ef-316">Add the following code at the end of the **QuizCtrl** controller to define the **nextQuestion** function in the **$scope** object.</span></span>

    <span data-ttu-id="832ef-317">(代码段- *AspNetWebApiSpa-Ex2-AngularQuizControllerNextQuestion*)</span><span class="sxs-lookup"><span data-stu-id="832ef-317">(Code Snippet - *AspNetWebApiSpa - Ex2 - AngularQuizControllerNextQuestion*)</span></span>

    [!code-javascript[Main](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/samples/sample18.js)]

    > [!NOTE]
    > <span data-ttu-id="832ef-318">此函数可检索下一个问题从**琐事**Web API 在上一练习中创建和附加到的问题数据**$scope**对象。</span><span class="sxs-lookup"><span data-stu-id="832ef-318">This function retrieves the next question from the **Trivia** Web API created in the previous exercise and attaches the question data to the **$scope** object.</span></span>
8. <span data-ttu-id="832ef-319">将下面的代码插入的结尾处**QuizCtrl**控制器定义**sendAnswer**函数中**$scope**对象。</span><span class="sxs-lookup"><span data-stu-id="832ef-319">Insert the following code at the end of the **QuizCtrl** controller to define the **sendAnswer** function in the **$scope** object.</span></span>

    <span data-ttu-id="832ef-320">(代码段- *AspNetWebApiSpa-Ex2-AngularQuizControllerSendAnswer*)</span><span class="sxs-lookup"><span data-stu-id="832ef-320">(Code Snippet - *AspNetWebApiSpa - Ex2 - AngularQuizControllerSendAnswer*)</span></span>

    [!code-javascript[Main](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/samples/sample19.js)]

    > [!NOTE]
    > <span data-ttu-id="832ef-321">此函数将发送到用户的所选回答**琐事**Web API，并将存储中的结果 – 即如果答案不正确，或未 – **$scope**对象。</span><span class="sxs-lookup"><span data-stu-id="832ef-321">This function sends the answer selected by the user to the **Trivia** Web API and stores the result –i.e. if the answer is correct or not– in the **$scope** object.</span></span>
    > 
    > <span data-ttu-id="832ef-322">**NextQuestion**和**sendAnswer**上面提供的函数使用 AngularJS **$http**对象抽象与通过 XMLHttpRequest Web API 的通信从浏览器的 JavaScript 对象。</span><span class="sxs-lookup"><span data-stu-id="832ef-322">The **nextQuestion** and **sendAnswer** functions from above use the AngularJS **$http** object to abstract the communication with the Web API via the XMLHttpRequest JavaScript object from the browser.</span></span> <span data-ttu-id="832ef-323">AngularJS 支持使更高级别的抽象，以执行针对通过 RESTful Api 资源的 CRUD 操作的另一个服务。</span><span class="sxs-lookup"><span data-stu-id="832ef-323">AngularJS supports another service that brings a higher level of abstraction to perform CRUD operations against a resource through RESTful APIs.</span></span> <span data-ttu-id="832ef-324">AngularJS **$resource**对象有提供高级行为而无需与之交互的操作方法**$http**对象。</span><span class="sxs-lookup"><span data-stu-id="832ef-324">The AngularJS **$resource** object has action methods which provide high-level behaviors without the need to interact with the **$http** object.</span></span> <span data-ttu-id="832ef-325">请考虑使用**$resource**方案需要 CRUD 模型的对象 (fore 信息，请参阅[$resource 文档](https://docs.angularjs.org/api/ngResource/service/$resource))。</span><span class="sxs-lookup"><span data-stu-id="832ef-325">Consider using the **$resource** object in scenarios that requires the CRUD model (fore information, see the [$resource documentation](https://docs.angularjs.org/api/ngResource/service/$resource)).</span></span>
9. <span data-ttu-id="832ef-326">下一步是创建定义测验的视图的 AngularJS 模板。</span><span class="sxs-lookup"><span data-stu-id="832ef-326">The next step is to create the AngularJS template that defines the view for the quiz.</span></span> <span data-ttu-id="832ef-327">若要执行此操作，打开**Index.cshtml**文件**视图 |主页**文件夹，然后替换其中的内容替换为以下代码。</span><span class="sxs-lookup"><span data-stu-id="832ef-327">To do this, open the **Index.cshtml** file inside the **Views | Home** folder and replace the content with the following code.</span></span>

    <span data-ttu-id="832ef-328">(代码段- *AspNetWebApiSpa-Ex2-GeekQuizView*)</span><span class="sxs-lookup"><span data-stu-id="832ef-328">(Code Snippet - *AspNetWebApiSpa - Ex2 - GeekQuizView*)</span></span>

    [!code-cshtml[Main](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/samples/sample20.cshtml)]

    > [!NOTE]
    > <span data-ttu-id="832ef-329">AngularJS 模板是使用来自模型和控制器的信息可将静态标记转换为该用户将看到在浏览器中的动态视图的声明性规范。</span><span class="sxs-lookup"><span data-stu-id="832ef-329">The AngularJS template is a declarative specification that uses information from the model and the controller to transform static markup into the dynamic view that the user sees in the browser.</span></span> <span data-ttu-id="832ef-330">AngularJS 元素和可以在模板中使用的元素属性的示例如下：</span><span class="sxs-lookup"><span data-stu-id="832ef-330">The following are examples of AngularJS elements and element attributes that can be used in a template:</span></span>
    > 
    > - <span data-ttu-id="832ef-331">**Ng 应用**指令指示 AngularJS 表示应用程序的根元素的 DOM 元素。</span><span class="sxs-lookup"><span data-stu-id="832ef-331">The **ng-app** directive tells AngularJS the DOM element that represents the root element of the application.</span></span>
    > - <span data-ttu-id="832ef-332">**Ng 控制器**指令将控制器附加到 DOM 指令的声明位置的点处。</span><span class="sxs-lookup"><span data-stu-id="832ef-332">The **ng-controller** directive attaches a controller to the DOM at the point where the directive is declared.</span></span>
    > - <span data-ttu-id="832ef-333">大括号表示法**{{}}**表示到控制器中定义的作用域属性的绑定。</span><span class="sxs-lookup"><span data-stu-id="832ef-333">The curly brace notation **{{ }}** denotes bindings to the scope properties defined in the controller.</span></span>
    > - <span data-ttu-id="832ef-334">**Ng 单击**指令用于调用以响应用户单击作用域中定义的函数。</span><span class="sxs-lookup"><span data-stu-id="832ef-334">The **ng-click** directive is used to invoke the functions defined in the scope in response to user clicks.</span></span>
10. <span data-ttu-id="832ef-335">打开**Site.css**文件**内容**文件夹和文件可供测验视图的外观和感觉的末尾添加以下突出显示的样式。</span><span class="sxs-lookup"><span data-stu-id="832ef-335">Open the **Site.css** file inside the **Content** folder and add the following highlighted styles at the end of the file to provide a look and feel for the quiz view.</span></span>

    <span data-ttu-id="832ef-336">(代码段- *AspNetWebApiSpa-Ex2-GeekQuizStyles*)</span><span class="sxs-lookup"><span data-stu-id="832ef-336">(Code Snippet - *AspNetWebApiSpa - Ex2 - GeekQuizStyles*)</span></span>

    [!code-css[Main](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/samples/sample21.css)]

<a id="Ex2Task2"></a>
#### <a name="task-2--running-the-solution"></a><span data-ttu-id="832ef-337">任务 2 – 运行解决方案</span><span class="sxs-lookup"><span data-stu-id="832ef-337">Task 2 – Running the Solution</span></span>

<span data-ttu-id="832ef-338">在将执行此任务使用新的用户的解决方案接口你使用 AngularJS 来回答一些测验问题生成。</span><span class="sxs-lookup"><span data-stu-id="832ef-338">In this task you will execute the solution using the new user interface you built with AngularJS to answer some of the quiz questions.</span></span>

1. <span data-ttu-id="832ef-339">按**F5**运行该解决方案。</span><span class="sxs-lookup"><span data-stu-id="832ef-339">Press **F5** to run the solution.</span></span>
2. <span data-ttu-id="832ef-340">注册新的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="832ef-340">Register a new user account.</span></span> <span data-ttu-id="832ef-341">若要执行此操作，请按照在练习 1 中，任务 3 中所述的注册步骤。</span><span class="sxs-lookup"><span data-stu-id="832ef-341">To do this, follow the registration steps described in Exercise 1, Task 3.</span></span>

    > [!NOTE]
    > <span data-ttu-id="832ef-342">如果使用从上一练习解决方案时，你可以登录之前创建的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="832ef-342">If you are using the solution from the previous exercise, you can log in with the user account you created before.</span></span>
3. <span data-ttu-id="832ef-343">**主页**页应显示，其中显示测验的第一个问题。</span><span class="sxs-lookup"><span data-stu-id="832ef-343">The **Home** page should appear, showing the first question of the quiz.</span></span> <span data-ttu-id="832ef-344">通过单击某个选项来回答问题。</span><span class="sxs-lookup"><span data-stu-id="832ef-344">Answer the question by clicking one of the options.</span></span> <span data-ttu-id="832ef-345">这将触发**sendAnswer**更早版本，定义的函数，它将发送到所选的选项**琐事**Web API。</span><span class="sxs-lookup"><span data-stu-id="832ef-345">This will trigger the **sendAnswer** function defined earlier, which sends the selected option to the **Trivia** Web API.</span></span>

    <span data-ttu-id="832ef-346">![回答问题](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image19.png "回答问题")</span><span class="sxs-lookup"><span data-stu-id="832ef-346">![Answering a question](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image19.png "Answering a question")</span></span>

    <span data-ttu-id="832ef-347">*回答问题*</span><span class="sxs-lookup"><span data-stu-id="832ef-347">*Answering a question*</span></span>
4. <span data-ttu-id="832ef-348">单击后的一个按钮，应显示答案。</span><span class="sxs-lookup"><span data-stu-id="832ef-348">After clicking one of the buttons, the answer should appear.</span></span> <span data-ttu-id="832ef-349">单击**下一个问题**以显示下面的问题。</span><span class="sxs-lookup"><span data-stu-id="832ef-349">Click **Next Question** to show the following question.</span></span> <span data-ttu-id="832ef-350">这将触发**nextQuestion**控制器中定义的函数。</span><span class="sxs-lookup"><span data-stu-id="832ef-350">This will trigger the **nextQuestion** function defined in the controller.</span></span>

    <span data-ttu-id="832ef-351">![请求的下一个问题](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image20.png "请求下一个问题")</span><span class="sxs-lookup"><span data-stu-id="832ef-351">![Requesting the next question](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image20.png "Requesting the next question")</span></span>

    <span data-ttu-id="832ef-352">*请求的下一个问题*</span><span class="sxs-lookup"><span data-stu-id="832ef-352">*Requesting the next question*</span></span>
5. <span data-ttu-id="832ef-353">应显示下一个问题。</span><span class="sxs-lookup"><span data-stu-id="832ef-353">The next question should appear.</span></span> <span data-ttu-id="832ef-354">继续根据需要多次通过回答问题。</span><span class="sxs-lookup"><span data-stu-id="832ef-354">Continue answering questions as many times as you want.</span></span> <span data-ttu-id="832ef-355">完成所有问题后，您应返回到第一个问题。</span><span class="sxs-lookup"><span data-stu-id="832ef-355">After completing all the questions you should return to the first question.</span></span>

    <span data-ttu-id="832ef-356">![另一个问题](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image21.png "另一个问题")</span><span class="sxs-lookup"><span data-stu-id="832ef-356">![Another question](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image21.png "Another question")</span></span>

    <span data-ttu-id="832ef-357">*下一个问题*</span><span class="sxs-lookup"><span data-stu-id="832ef-357">*Next question*</span></span>
6. <span data-ttu-id="832ef-358">返回到 Visual Studio，然后按**SHIFT + F5**来停止调试。</span><span class="sxs-lookup"><span data-stu-id="832ef-358">Go back to Visual Studio and press **SHIFT + F5** to stop debugging.</span></span>

<a id="Ex2Task3"></a>
#### <a name="task-3--creating-a-flip-animation-using-css3"></a><span data-ttu-id="832ef-359">任务 3 – 创建使用 CSS3 翻转动画</span><span class="sxs-lookup"><span data-stu-id="832ef-359">Task 3 – Creating a Flip Animation Using CSS3</span></span>

<span data-ttu-id="832ef-360">在此任务将使用 CSS3 属性通过添加翻转效果时问题答案和检索下一个问题时执行丰富的动画。</span><span class="sxs-lookup"><span data-stu-id="832ef-360">In this task you will use CSS3 properties to perform rich animations by adding a flip effect when a question is answered and when the next question is retrieved.</span></span>

1. <span data-ttu-id="832ef-361">在**解决方案资源管理器**，右键单击**内容**文件夹**GeekQuiz**项目，然后选择**添加 |现有项...**.</span><span class="sxs-lookup"><span data-stu-id="832ef-361">In **Solution Explorer**, right-click the **Content** folder of the **GeekQuiz** project and select **Add | Existing Item...**.</span></span>

    <span data-ttu-id="832ef-362">![将现有项添加到内容文件夹](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image22.png "将现有项添加到内容文件夹")</span><span class="sxs-lookup"><span data-stu-id="832ef-362">![Adding an existing item to the Content folder](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image22.png "Adding an existing item to the Content folder")</span></span>

    <span data-ttu-id="832ef-363">*将现有项添加到内容文件夹*</span><span class="sxs-lookup"><span data-stu-id="832ef-363">*Adding an existing item to the Content folder*</span></span>
2. <span data-ttu-id="832ef-364">在**添加现有项**对话框框中，导航到**源/资产**文件夹，然后选择**Flip.css**。</span><span class="sxs-lookup"><span data-stu-id="832ef-364">In the **Add Existing Item** dialog box, navigate to the **Source/Assets** folder and select **Flip.css**.</span></span> <span data-ttu-id="832ef-365">单击 **“添加”**。</span><span class="sxs-lookup"><span data-stu-id="832ef-365">Click **Add**.</span></span>

    <span data-ttu-id="832ef-366">![从资产添加 Flip.css 文件](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image23.png "从资产添加 Flip.css 文件")</span><span class="sxs-lookup"><span data-stu-id="832ef-366">![Adding the Flip.css file from Assets](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image23.png "Adding the Flip.css file from Assets")</span></span>

    <span data-ttu-id="832ef-367">*从资产添加 Flip.css 文件*</span><span class="sxs-lookup"><span data-stu-id="832ef-367">*Adding the Flip.css file from Assets*</span></span>
3. <span data-ttu-id="832ef-368">打开**Flip.css**文件您刚刚添加并检查其内容。</span><span class="sxs-lookup"><span data-stu-id="832ef-368">Open the **Flip.css** file you just added and inspect its content.</span></span>
4. <span data-ttu-id="832ef-369">找到**翻转转换**注释。</span><span class="sxs-lookup"><span data-stu-id="832ef-369">Locate the **flip transformation** comment.</span></span> <span data-ttu-id="832ef-370">下面的注释样式使用 CSS**透视**和**rotateY**转换生成&quot;卡翻转&quot;效果。</span><span class="sxs-lookup"><span data-stu-id="832ef-370">The styles below that comment use the CSS **perspective** and **rotateY** transformations to generate a &quot;card flip&quot; effect.</span></span>

    [!code-css[Main](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/samples/sample22.css)]
5. <span data-ttu-id="832ef-371">找到**期间翻转背面窗格隐藏**注释。</span><span class="sxs-lookup"><span data-stu-id="832ef-371">Locate the **hide back of pane during flip** comment.</span></span> <span data-ttu-id="832ef-372">该注释下面的样式时它们将面临离开查看器通过设置隐藏的平面的后端**背面可见性**CSS 属性*隐藏*。</span><span class="sxs-lookup"><span data-stu-id="832ef-372">The style below that comment hides the back-side of the faces when they are facing away from the viewer by setting the **backface-visibility** CSS property to *hidden*.</span></span>

    [!code-css[Main](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/samples/sample23.css)]
6. <span data-ttu-id="832ef-373">打开**BundleConfig.cs**文件**应用\_启动**文件夹并添加对引用**Flip.css**文件中 **&quot;~/Content/css&quot;** 样式捆绑包</span><span class="sxs-lookup"><span data-stu-id="832ef-373">Open the **BundleConfig.cs** file inside the **App\_Start** folder and add the reference to the **Flip.css** file in the **&quot;~/Content/css&quot;** style bundle</span></span>

    [!code-csharp[Main](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/samples/sample24.cs)]
7. <span data-ttu-id="832ef-374">按**F5**运行解决方案，并登录你的凭据。</span><span class="sxs-lookup"><span data-stu-id="832ef-374">Press **F5** to run the solution and log in with your credentials.</span></span>
8. <span data-ttu-id="832ef-375">通过单击某个选项来回答问题。</span><span class="sxs-lookup"><span data-stu-id="832ef-375">Answer a question by clicking one of the options.</span></span> <span data-ttu-id="832ef-376">视图之间转换时，请注意翻转的效果。</span><span class="sxs-lookup"><span data-stu-id="832ef-376">Notice the flip effect when transitioning between views.</span></span>

    <span data-ttu-id="832ef-377">![回答的问题将有翻转效果](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image24.png "回答的问题将有翻转的效果")</span><span class="sxs-lookup"><span data-stu-id="832ef-377">![Answering a question with the flip effect](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image24.png "Answering a question with the flip effect")</span></span>

    <span data-ttu-id="832ef-378">*回答的问题将有翻转的效果*</span><span class="sxs-lookup"><span data-stu-id="832ef-378">*Answering a question with the flip effect*</span></span>
9. <span data-ttu-id="832ef-379">单击**下一个问题**检索下面的问题。</span><span class="sxs-lookup"><span data-stu-id="832ef-379">Click **Next Question** to retrieve the following question.</span></span> <span data-ttu-id="832ef-380">翻转效果应该再次出现。</span><span class="sxs-lookup"><span data-stu-id="832ef-380">The flip effect should appear again.</span></span>

    <span data-ttu-id="832ef-381">![检索的翻转的效果与下面的问题](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image25.png "检索的翻转的效果与下面的问题")</span><span class="sxs-lookup"><span data-stu-id="832ef-381">![Retrieving the following question with the flip effect](build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs/_static/image25.png "Retrieving the following question with the flip effect")</span></span>

    <span data-ttu-id="832ef-382">*检索的翻转的效果与下面的问题*</span><span class="sxs-lookup"><span data-stu-id="832ef-382">*Retrieving the following question with the flip effect*</span></span>

* * *

<a id="Summary"></a>
## <a name="summary"></a><span data-ttu-id="832ef-383">摘要</span><span class="sxs-lookup"><span data-stu-id="832ef-383">Summary</span></span>

<span data-ttu-id="832ef-384">通过完成本动手实验你已学习如何：</span><span class="sxs-lookup"><span data-stu-id="832ef-384">By completing this hands-on lab you have learned how to:</span></span>

- <span data-ttu-id="832ef-385">创建 ASP.NET Web API 控制器使用 ASP.NET 基架</span><span class="sxs-lookup"><span data-stu-id="832ef-385">Create an ASP.NET Web API controller using ASP.NET Scaffolding</span></span>
- <span data-ttu-id="832ef-386">实现一个 Web API 获取操作，以便检索下一步的测验问题</span><span class="sxs-lookup"><span data-stu-id="832ef-386">Implement a Web API Get action to retrieve the next quiz question</span></span>
- <span data-ttu-id="832ef-387">实现 Web API 后操作来存储测验答案</span><span class="sxs-lookup"><span data-stu-id="832ef-387">Implement a Web API Post action to store the quiz answers</span></span>
- <span data-ttu-id="832ef-388">从 Visual Studio 包管理器控制台安装 AngularJS</span><span class="sxs-lookup"><span data-stu-id="832ef-388">Install AngularJS from the Visual Studio Package Manager Console</span></span>
- <span data-ttu-id="832ef-389">实现 AngularJS 模板和控制器</span><span class="sxs-lookup"><span data-stu-id="832ef-389">Implement AngularJS templates and controllers</span></span>
- <span data-ttu-id="832ef-390">CSS3 转换用于执行动画效果</span><span class="sxs-lookup"><span data-stu-id="832ef-390">Use CSS3 transitions to perform animation effects</span></span>