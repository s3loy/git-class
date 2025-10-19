---
title: 'Git 入门教程'
theme: apple-basic
colorSchema: 'light'
transition: slide-down
---

<div class="pt-10 text-center">
  <img src="/git-icon.png" class="inline-block w-28 h-28 mb-4" />
  
  <h1 class="text-7xl font-bold mb-6">Git 入门教程</h1>
  
  <p class="text-2xl text-gray-600 mb-12">
    一个为开发者设计的版本控制系统
  </p>
  
  <div class="text-xl text-gray-500">
    软研部运维组
    <div class="mt-2">2025年10月19日</div>
  </div>
</div>

---
transition: slide-up
layout: default
---

# 学习目标

<div class="grid grid-cols-2 gap-8 mt-8">
  <div v-motion :initial="{ x: -80, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }" class="p-4 bg-gradient-to-br from-blue-50 to-blue-100 rounded-lg shadow-sm">
    <div class="text-4xl mb-3">📝</div>
    <h3 class="font-bold text-lg mb-2">掌握 Git 的基本操作</h3>
    <p class="text-sm opacity-75">保存代码、查看历史、回退版本</p>
  </div>

  <div v-motion :initial="{ x: 80, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }" class="p-4 bg-gradient-to-br from-green-50 to-green-100 rounded-lg shadow-sm">
    <div class="text-4xl mb-3">🌿</div>
    <h3 class="font-bold text-lg mb-2">学会使用分支</h3>
    <p class="text-sm opacity-75">开发新功能时不影响主代码</p>
  </div>

  <div v-motion :initial="{ y: 80, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }" class="col-span-2 p-4 bg-gradient-to-br from-purple-50 to-purple-100 rounded-lg shadow-sm">
    <div class="text-4xl mb-3">👥</div>
    <h3 class="font-bold text-lg mb-2">了解团队协作和解决常见问题</h3>
    <p class="text-sm opacity-75">从 GitHub 下载代码、处理冲突</p>
  </div>
</div>

---
layout: quote
transition: fade-out
---

# 什么是"版本控制"？
<br>

> 
> "一种记录一个或若干文件内容变化，以便将来查阅特定版本修订情况的系统。"
> 
>                                                                           --《 Pro Git 》
<br>
<br>

简单来说，它就像是代码的"**时光机**"🕰️

---
transition: slide-left
---

# 为什么需要版本控制？

<div class="grid grid-cols-2 gap-6 mt-6">
  <div v-motion :initial="{ x: -50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }" class="p-5 bg-red-50 rounded-xl border-2 border-red-200">
    <h2 class="text-2xl mb-4">😱 没有版本控制的噩梦</h2>
    <div class="space-y-2 text-sm">
      <div class="p-2 bg-white rounded">📄 final.docx</div>
      <div class="text-xl text-center">↓</div>
      <div class="p-2 bg-white rounded">📄 final(1).docx</div>
      <div class="text-xl text-center">↓</div>
      <div class="p-2 bg-white rounded">📄 final(1)_final.docx</div>
      <div class="text-xl text-center">↓</div>
      <div class="p-2 bg-white rounded">📄 final(1)_final最终版(2).docx</div>
    </div>
    <div class="mt-4 text-sm opacity-75">
      ❌ 不小心删除代码<br>
      ❌ 多人互相覆盖<br>
      ❌ 找不回历史版本
    </div>
  </div>

  <div v-motion :initial="{ x: 50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }" class="p-5 bg-gradient-to-br from-green-50 to-emerald-100 rounded-xl border-2 border-green-200">
    <h2 class="text-2xl mb-4">✨ 有了 Git 之后</h2>
    <div class="space-y-3">
      <div class="flex items-center gap-3">
        <div class="text-2xl">📜</div>
        <div class="text-sm">完整的历史记录<br><span class="opacity-60">每一次修改都可追溯</span></div>
      </div>
      <div class="flex items-center gap-3">
        <div class="text-2xl">🔄</div>
        <div class="text-sm">随时回退<br><span class="opacity-60">时光机般的体验</span></div>
      </div>
      <div class="flex items-center gap-3">
        <div class="text-2xl">👥</div>
        <div class="text-sm">多人协作井然有序<br><span class="opacity-60">自动合并代码</span></div>
      </div>
      <div class="flex items-center gap-3">
        <div class="text-2xl">🌿</div>
        <div class="text-sm">分支并行开发<br><span class="opacity-60">互不干扰</span></div>
      </div>
    </div>
  </div>
</div>

---
layout: default
transition: slide-down
---

# Git 上手
<div v-motion :initial="{ scale: 0.9, opacity: 0 }" :enter="{ scale: 1, opacity: 1, transition: { delay: 800 } }" class="mt-12">
  <div class="max-w-4xl mx-auto p-8 bg-gradient-to-br from-blue-50 to-cyan-50 rounded-2xl shadow-lg border-2 border-blue-200">
    <h2 class="text-3xl font-bold mb-6 flex items-center gap-3">
      <span class="text-xl">🎯</span>
      <span>要点</span>
    </h2>
    <div class="space-y-4">
      <div class="flex items-start gap-4 p-4 bg-white rounded-xl shadow-sm">
        <span class="text-2xl">1️⃣</span>
        <div>
          <div class="text-xl font-bold">理解三个工作区域</div>
          <div class="text-sm opacity-75 mt-1">工作区 → 暂存区 → 本地仓库</div>
        </div>
      </div>
      <div class="flex items-start gap-4 p-4 bg-white rounded-xl shadow-sm">
        <span class="text-3xl">2️⃣</span>
        <div>
          <div class="text-xl font-bold">掌握基础命令</div>
          <div class="text-sm opacity-75 mt-1">add, commit, status, log</div>
        </div>
      </div>
      <div class="flex items-start gap-4 p-4 bg-white rounded-xl shadow-sm">
        <span class="text-3xl">3️⃣</span>
        <div>
          <div class="text-xl font-bold">建立正确的工作流程</div>
          <div class="text-sm opacity-75 mt-1">从实践中学习</div>
        </div>
      </div>
    </div>
  </div>
</div>

---
transition: slide-right
---
 
# Git 的三个工作区域

<div class="flex items-center gap-3 text-lg my-8">
  <div class="flex-1 p-3 bg-blue-50 rounded">
    <div class="font-bold mb-1">🗂️ 工作区</div>
    <div class="text-sm opacity-75">你正在编辑的文件</div>
  </div>
  <div class="text-2xl">→</div>
  <div class="flex-1 p-3 bg-yellow-50 rounded">
    <div class="font-bold mb-1">📦 暂存区</div>
    <div class="text-sm opacity-75">准备提交的文件</div>
  </div>
  <div class="text-2xl">→</div>
  <div class="flex-1 p-3 bg-green-50 rounded">
    <div class="font-bold mb-1">📚 本地仓库</div>
    <div class="text-sm opacity-75">已保存的历史版本</div>
  </div>
</div>

<div class="p-4 bg-gray-100 rounded">
  <code>git add</code> 将文件从工作区添加到暂存区<br>
  <code>git commit</code> 将暂存区的文件提交到仓库
</div>

---
layout: center
---

<div class="text-center">
  <div class="text-6xl mb-6">📝</div>
  <h1 class="text-4xl font-bold text-blue-600 mb-3">第一部分：基础入门</h1>
  <p class="text-xl opacity-60">从零开始学习 Git</p>
</div>

---
transition: fade-out
---

# 安装与配置 Git

<div class="grid grid-cols-2 gap-6">
  <div v-motion :initial="{ y: -50, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-4 bg-blue-50 rounded-lg">
      <h2 class="text-xl mb-4 flex items-center gap-2">
        <span class="text-3xl">📥</span>
        <span>安装 Git</span>
      </h2>
      <div class="space-y-3 text-sm">
        <div class="p-3 bg-white rounded-lg shadow-sm">
          <div class="font-bold flex items-center gap-2">
            <span>🪟</span> Windows
          </div>
          <a href="https://git-scm.com/download/win" class="text-blue-600 text-xs">git-scm.com/download/win</a>
          <div class="text-xs opacity-75 mt-1">一路"下一步"安装即可</div>
        </div>
        <div class="p-3 bg-white rounded-lg shadow-sm">
          <div class="font-bold flex items-center gap-2">
            <span>🍎</span> Mac
          </div>
          <code class="text-xs bg-gray-100 px-2 py-1 rounded">brew install git</code>
        </div>
        <div class="p-3 bg-white rounded-lg shadow-sm">
          <div class="font-bold flex items-center gap-2">
            <span>🐧</span> Linux ( ubuntu )
          </div>
          <code class="text-xs bg-gray-100 px-2 py-1 rounded">sudo apt-get install git</code>
        </div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ y: 50, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-4 bg-gradient-to-br from-purple-50 to-pink-50 rounded-lg">
      <h2 class="text-xl mb-4 flex items-center gap-2">
        <span class="text-3xl">⚙️</span>
        <span>首次配置</span>
      </h2>
      <div class="bg-pink-50 border border-pink-300 text-gray-800 p-4 rounded-lg font-mono text-sm">
        <div class="opacity-50"># 设置你的名字和邮箱</div>
        <div class="mt-2">git config --global user.name "张三"</div>
        <div class="mt-1">git config --global user.email "zhangsan@example.com"</div>
      </div>
      <div class="mt-3 p-2 bg-yellow-100 rounded text-xs flex items-start gap-2">
        <span>💡</span>
        <span>这些信息会显示在你的每次提交中</span>
      </div>
    </div>
  </div>
</div>

---
transition: fade
---

# `git init` - 创建仓库

<div class="grid grid-cols-2 gap-8 mt-8">
  <div v-motion :initial="{ scale: 0.8, opacity: 0 }" :enter="{ scale: 1, opacity: 1, transition: { delay: 800 } }">
    <div class="relative p-6 bg-gradient-to-br from-blue-50 to-cyan-50 rounded-xl border-2 border-blue-200">
      <div class="absolute -top-4 -left-4 w-12 h-12 bg-blue-500 rounded-full flex items-center justify-center text-white text-xl font-bold shadow-lg">1</div>
      <h2 class="text-xl mb-4 font-bold">🌱 从零开始</h2>
      <div class="bg-blue-50 border border-blue-300 text-gray-800 p-4 rounded-lg font-mono text-sm">
        <div class="opacity-50"># 创建新项目</div>
        <div class="mt-2">mkdir my-project</div>
        <div>cd my-project</div>
        <div class="mt-2 font-bold">git init</div>
      </div>
      <div class="mt-3 p-3 bg-white rounded-lg text-sm flex items-start gap-2">
        <span class="text-xl">✅</span>
        <div>
          <div class="font-bold">创建 .git 目录</div>
          <div class="text-xs opacity-75">这就是 Git 仓库的核心</div>
        </div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ scale: 0.8, opacity: 0 }" :enter="{ scale: 1, opacity: 1, transition: { delay: 800 } }">
    <div class="relative p-6 bg-gradient-to-br from-green-50 to-emerald-50 rounded-xl border-2 border-green-200">
      <div class="absolute -top-4 -left-4 w-12 h-12 bg-green-500 rounded-full flex items-center justify-center text-white text-xl font-bold shadow-lg">2</div>
      <h2 class="text-xl mb-4 font-bold">📦 克隆现有项目</h2>
      <div class="bg-green-50 border border-green-300 text-gray-800 p-4 rounded-lg font-mono text-sm">
        <div class="opacity-50"># 从 GitHub 克隆</div>
        <div class="mt-2">git clone https://github.com/</div>
        <div class="ml-4">username/repository.git</div>
      </div>
      <div class="mt-3 p-3 bg-white rounded-lg text-sm flex items-start gap-2">
        <span class="text-xl">✅</span>
        <div>
          <div class="font-bold">自动下载</div>
          <div class="text-xs opacity-75">完整的项目和历史记录</div>
        </div>
      </div>
    </div>
  </div>
</div>

---
transition: slide-left
---

# `.gitignore` - 告诉 Git 忽略哪些文件

<div class="grid grid-cols-2 gap-6">
  <div v-motion :initial="{ x: -50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }">
    <h3 class="text-lg font-bold mb-3 flex items-center gap-2">
      <span class="text-2xl">❌</span>
      <span>不该提交的文件</span>
    </h3>
    <div class="space-y-2">
      <div class="p-3 bg-red-50 rounded-lg border-l-4 border-red-400">
        <div class="font-bold text-sm">编译产物</div>
        <div class="text-xs opacity-75 font-mono mt-1">target/, *.exe, *.o</div>
      </div>
<div class="p-3 bg-orange-50 rounded-lg border-l-4 border-orange-400">
<div class="font-bold text-sm">日志文件</div>
<div class="text-xs opacity-75 font-mono mt-1">*.log, debug.log</div>
      </div>
      <div class="p-3 bg-yellow-50 rounded-lg border-l-4 border-yellow-400">
        <div class="font-bold text-sm">系统文件</div>
        <div class="text-xs opacity-75 font-mono mt-1">.DS_Store, Thumbs.db</div>
      </div>
      <div class="p-3 bg-purple-50 rounded-lg border-l-4 border-purple-400">
        <div class="font-bold text-sm">编辑器配置</div>
        <div class="text-xs opacity-75 font-mono mt-1">.vscode/, .idea/</div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ x: 50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }">
    <h3 class="text-lg font-bold mb-3 flex items-center gap-2">
      <span class="text-2xl">📝</span>
      <span>创建 .gitignore 文件</span>
    </h3>
    <div class="bg-blue-50 border border-blue-300 text-gray-800 p-4 rounded-lg font-mono text-sm">
      <div class="opacity-50"># 编译产物</div>
      <div>/target/</div>
      <div class="mt-2 opacity-50"># 日志</div>
      <div>*.log</div>
      <div class="mt-2 opacity-50"># 系统文件</div>
      <div>.DS_Store</div>
    </div>
    <div class="mt-3 p-3 bg-blue-50 rounded-lg text-xs flex items-start gap-2">
      <span>💡</span>
      <div>
        <span class="font-bold">小提示：</span>
        GitHub 为各种语言准备了模板<br>
        搜索 <code class="bg-white px-1 rounded">"github gitignore rust"</code>
      </div>
    </div>
  </div>
</div>
---
transition: slide-up
---

# 基础工作流演示

<div class="grid grid-cols-2 gap-5 mt-4">
  <div v-motion :initial="{ scale: 0.9, opacity: 0 }" :enter="{ scale: 1, opacity: 1, transition: { delay: 800 } }">
    <div class="p-5 bg-gradient-to-br from-blue-50 to-cyan-50 rounded-xl shadow-md">
      <div class="flex items-center gap-3 mb-3">
        <div class="w-8 h-8 bg-blue-500 rounded-full flex items-center justify-center text-white font-bold">1</div>
        <h2 class="text-lg font-bold">创建文件</h2>
      </div>
      <div class="bg-blue-50 border border-blue-300 text-gray-800 p-4 rounded-lg font-mono text-xs">
        <div class="opacity-50"># 创建 README.md</div>
        <div>echo "# My Rust Project" &gt; README.md</div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ scale: 0.9, opacity: 0 }" :enter="{ scale: 1, opacity: 1, transition: { delay: 800 } }">
    <div class="p-5 bg-gradient-to-br from-purple-50 to-purple-100 rounded-xl shadow-md">
      <div class="flex items-center gap-3 mb-3">
        <div class="w-8 h-8 bg-purple-500 rounded-full flex items-center justify-center text-white font-bold">2</div>
        <h2 class="text-lg font-bold">查看状态</h2>
      </div>
      <div class="bg-purple-50 border border-purple-300 text-gray-800 p-4 rounded-lg font-mono text-xs">
        <div>git status</div>
        <div class="text-xs mt-2 opacity-50"># 显示未追踪的文件（红色）</div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ scale: 0.9, opacity: 0 }" :enter="{ scale: 1, opacity: 1, transition: { delay: 800 } }">
    <div class="p-5 bg-gradient-to-br from-green-50 to-emerald-100 rounded-xl shadow-md">
      <div class="flex items-center gap-3 mb-3">
        <div class="w-8 h-8 bg-green-500 rounded-full flex items-center justify-center text-white font-bold">3</div>
        <h2 class="text-lg font-bold">添加到暂存区</h2>
      </div>
      <div class="bg-green-50 border border-green-300 text-gray-800 p-4 rounded-lg font-mono text-xs">
        <div>git add .</div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ scale: 0.9, opacity: 0 }" :enter="{ scale: 1, opacity: 1, transition: { delay: 800 } }">
    <div class="p-5 bg-gradient-to-br from-orange-50 to-orange-100 rounded-xl shadow-md">
      <div class="flex items-center gap-3 mb-3">
        <div class="w-8 h-8 bg-orange-500 rounded-full flex items-center justify-center text-white font-bold">4</div>
        <h2 class="text-lg font-bold">提交</h2>
      </div>
      <div class="bg-orange-50 border border-orange-300 text-gray-800 p-4 rounded-lg font-mono text-xs">
        <div>git commit -m "feat: 初始化项目"</div>
      </div>
    </div>
  </div>
</div>
---
transition: slide-right
---

# `git status` - 查看当前状态

<div class="grid grid-cols-2 gap-6 mt-4">
  <div v-motion :initial="{ x: -50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-5 bg-gradient-to-br from-blue-50 to-cyan-50 rounded-xl shadow-sm">
      <h2 class="text-xl font-bold mb-4 flex items-center gap-2">
        <span class="text-3xl">📊</span>
        <span>命令与输出</span>
      </h2>
      <div class="bg-blue-50 border border-blue-300 text-gray-800 p-4 rounded-lg font-mono text-xs space-y-2">
        <div class="font-bold">$ git status</div>
        <div class="opacity-75">On branch main</div>
        <div class="text-green-600 font-bold">Changes to be committed:</div>
        <div class="text-green-600 ml-2">new file:   README.md</div>
        <div class="mt-2 text-red-600 font-bold">Changes not staged:</div>
        <div class="text-red-600 ml-2">modified:   src/main.rs</div>
        <div class="mt-2 opacity-75">Untracked files:</div>
        <div class="text-red-600 ml-2">src/lib.rs</div>
      </div>
    </div>
</div>

  <div v-motion :initial="{ x: 50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-5 bg-gradient-to-br from-purple-50 to-pink-50 rounded-xl shadow-sm">
      <h2 class="text-xl font-bold mb-4 flex items-center gap-2">
        <span class="text-3xl">🎨</span>
        <span>三种文件状态</span>
      </h2>
      <div class="space-y-2 text-sm">
        <div class="p-3 bg-green-100 rounded-lg border-l-4 border-green-500 flex items-center gap-2">
          <span class="text-xl">✅</span>
          <div>
            <span class="font-bold text-green-600">绿色</span>
            <div class="text-xs opacity-75">已 add,准备提交</div>
          </div>
        </div>
        <div class="p-3 bg-red-100 rounded-lg border-l-4 border-red-500 flex items-center gap-2">
          <span class="text-xl">⚠️</span>
          <div>
            <span class="font-bold text-red-600">红色</span>
            <div class="text-xs opacity-75">修改了但还没 add</div>
          </div>
        </div>
        <div class="p-3 bg-gray-100 rounded-lg border-l-4 border-gray-500 flex items-center gap-2">
          <span class="text-xl">📄</span>
          <div>
            <span class="font-bold">未追踪</span>
            <div class="text-xs opacity-75">Git 还不认识的新文件</div>
          </div>
        </div>
      </div>
    </div>
  </div>

</div>

<div v-motion :initial="{ y: 30, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }" class="mt-6 p-4 bg-blue-50 rounded-xl border-l-4 border-blue-400 flex items-start gap-3">
  <span class="text-3xl">💡</span>
  <div>
    <div class="font-bold text-lg">最佳实践</div>
    <div class="text-sm opacity-75">养成习惯,每次操作前后都 <code class="bg-white px-2 py-1 rounded">git status</code> 看一眼</div>
  </div>
</div>

---
transition: slide-left
---

# `git diff` - 看看改了什么

<div class="grid grid-cols-2 gap-6 mt-4">

  <div v-motion :initial="{ y: -50, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-5 bg-gradient-to-br from-purple-50 to-purple-100 rounded-xl shadow-sm">
      <h2 class="text-xl font-bold mb-4 flex items-center gap-2">
        <span class="text-3xl">🔍</span>
        <span>查看改动</span>
      </h2>
      <div class="space-y-3">
        <div class="bg-purple-50 border border-purple-300 text-gray-800 p-3 rounded-lg font-mono text-sm">
          <div class="opacity-50"># 工作区的改动</div>
          <div>git diff</div>
        </div>
        <div class="bg-purple-50 border border-purple-300 text-gray-800 p-3 rounded-lg font-mono text-sm">
          <div class="opacity-50"># 暂存区的改动</div>
          <div>git diff --staged</div>
        </div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ y: -50, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-5 bg-gradient-to-br from-green-50 to-emerald-100 rounded-xl shadow-sm">
      <h2 class="text-xl font-bold mb-4 flex items-center gap-2">
        <span class="text-3xl">📝</span>
        <span>输出示例</span>
      </h2>
      <div class="bg-green-50 border border-green-300 p-4 rounded-lg font-mono text-sm">
        <div class="text-red-600 font-bold">- let x = 10;</div>
        <div class="text-green-600 font-bold">+ let x = 20;</div>
        <div class="mt-3 text-xs opacity-75">
          <div class="text-red-600">红色:删掉的代码</div>
          <div class="text-green-600">绿色:新加的代码</div>
        </div>
      </div>
    </div>
  </div>

</div>

<div v-motion :initial="{ y: 30, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }" class="mt-6 p-5 bg-yellow-50 rounded-xl border-l-4 border-yellow-400 flex items-start gap-3">
  <span class="text-4xl">💡</span>
  <div>
    <div class="font-bold text-lg">VSCode 更方便</div>
    <div class="text-sm opacity-75">在源代码管理面板点击文件就能看到<span class="font-bold text-yellow-600">可视化对比</span></div>
  </div>
</div>

---
transition: fade
---

# `git log` - 查看提交历史

<div class="grid grid-cols-2 gap-6 mt-4">

  <div v-motion :initial="{ x: -50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-5 bg-gradient-to-br from-blue-50 to-cyan-50 rounded-xl shadow-sm">
      <h2 class="text-xl font-bold mb-4 flex items-center gap-2">
        <span class="text-3xl">📜</span>
        <span>查看历史</span>
      </h2>
      <div class="bg-blue-50 border border-blue-300 text-gray-800 p-4 rounded-lg font-mono text-sm">
        <div class="opacity-50"># ⭐ 推荐:简洁明了</div>
        <div>git log --oneline</div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ x: 50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-5 bg-gradient-to-br from-purple-50 to-purple-100 rounded-xl shadow-sm">
      <h2 class="text-xl font-bold mb-4 flex items-center gap-2">
        <span class="text-3xl">📊</span>
        <span>输出示例</span>
      </h2>
      <div class="bg-purple-50 border border-purple-300 text-gray-800 p-4 rounded-lg font-mono text-sm space-y-1">
        <div>
          <span class="text-orange-600 font-bold">a3f5b2c</span>
          <span class="text-green-600"> feat: 添加错误处理</span>
        </div>
        <div>
          <span class="text-orange-600 font-bold">7d8e9f0</span>
          <span class="text-blue-600"> fix: 修复编译警告</span>
        </div>
        <div>
          <span class="text-orange-600 font-bold">b2c4d5e</span>
          <span class="text-purple-600"> feat: 初始化项目</span>
        </div>
      </div>
    </div>
  </div>

</div>

<div v-motion :initial="{ y: 30, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }" class="mt-6 p-5 bg-yellow-50 rounded-xl border-l-4 border-yellow-400 flex items-start gap-3">
  <span class="text-4xl">💡</span>
  <div>
    <div class="font-bold text-lg">小提示</div>
    <div class="text-sm opacity-75">每个提交都有<span class="font-bold text-yellow-600">唯一编号</span>(如 a3f5b2c)</div>
    <div class="text-sm opacity-75 mt-1">VSCode可以看<span class="font-bold text-yellow-600">图形化历史</span></div>
  </div>
</div>

---
layout: center
class: text-center
transition: slide-down
---

<div class="text-center">
  <div class="text-6xl mb-6">🌿</div>
  <h1 class="text-4xl font-bold text-green-600 mb-3">第二部分：分支管理</h1>
  <p class="text-xl opacity-60">Git 的精髓所在</p>
</div>

---
transition: fade-out
---

# 为什么需要分支？

<div v-motion :initial="{ scale: 0.9, opacity: 0 }" :enter="{ scale: 1, opacity: 1, transition: { delay: 800 } }">
  <div class="p-4 bg-gradient-to-r from-red-50 to-orange-50 rounded-xl mb-6 border-2 border-red-200">
    <div class="flex items-center gap-4">
      <div class="text-5xl">😱</div>
      <div>
        <div class="font-bold text-lg mb-2">没有分支的困境</div>
        <div class="text-sm opacity-75">
          想象写论文:<code class="bg-white px-2 py-1 rounded">论文.docx</code> → 
          <code class="bg-white px-2 py-1 rounded">论文_新版.docx</code> → 
          <code class="bg-white px-2 py-1 rounded">论文_最新版.docx</code>
        </div>
        <div class="mt-2 text-xs">
          ❌ 想尝试新想法却怕改坏 &nbsp; ❌ 多人只能轮流修改
        </div>
      </div>
    </div>
  </div>
</div>

<div v-motion :initial="{ y: 50, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }">
  <div class="p-5 bg-gradient-to-br from-green-50 to-emerald-50 rounded-xl border-2 border-green-200">
    <h2 class="text-2xl mb-4 flex items-center gap-2">
      <span>✨</span>
      <span>有了分支</span>
    </h2>
    <div class="bg-green-50 border border-green-300 text-gray-800 p-4 rounded-lg font-mono text-sm mb-4">
      <div class="flex items-center gap-2">
        <span class="font-bold text-blue-600">main 分支</span>
        <span>———————————————→</span>
        <span class="text-green-600">(稳定的主版本)</span>
      </div>
      <div class="ml-8 flex items-center gap-2 mt-2">
        <span>\</span>
      </div>
      <div class="ml-12 flex items-center gap-2">
        <span class="font-bold text-purple-600">实验分支</span>
        <span>——→</span>
        <span class="text-orange-600">(随便试新想法,不怕搞坏)</span>
      </div>
    </div>
    <div class="grid grid-cols-3 gap-3 text-sm">
      <div class="p-3 bg-white rounded-lg shadow-sm">
        <div class="font-bold mb-1">✍️ 步骤 1</div>
        <div class="text-xs opacity-75">在 main 分支写作业</div>
      </div>
      <div class="p-3 bg-white rounded-lg shadow-sm">
        <div class="font-bold mb-1">🌿 步骤 2</div>
        <div class="text-xs opacity-75">创建新分支来创新和尝试</div>
      </div>
      <div class="p-3 bg-white rounded-lg shadow-sm">
        <div class="font-bold mb-1">✅ 步骤 3</div>
        <div class="text-xs opacity-75">好用就合并,不好就删</div>
      </div>
    </div>

  </div>
</div>

---
transition: slide-right
---

# 理解分支

<div class="grid grid-cols-2 gap-6 mt-4">

  <div v-motion :initial="{ x: -50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-5 bg-gradient-to-br from-blue-50 to-cyan-50 rounded-xl shadow-sm">
      <h2 class="text-xl font-bold mb-4 flex items-center gap-2">
        <span>什么是分支?</span>
      </h2>
      <p class="text-sm mb-4">分支就像给代码<span class="font-bold text-blue-600">"贴书签"</span>,告诉 Git 这是哪个版本</p>
      <div class="bg-blue-50 border border-blue-300 text-gray-800 p-4 rounded-lg font-mono text-xs">
        <div class="flex items-center gap-1">
          <span class="text-blue-600 font-bold">提交1</span>
          <span>←</span>
          <span class="text-green-600 font-bold">提交2</span>
          <span>←</span>
          <span class="text-purple-600 font-bold">提交3</span>
          <span>←</span>
          <span class="text-orange-600 font-bold">main</span>
        </div>
        <div class="mt-2 ml-20 opacity-75">↑</div>
        <div class="ml-16 text-indigo-600 font-bold">新分支</div>
        <div class="text-xs opacity-50 mt-2">(指向同一个地方)</div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ x: 50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-5 bg-gradient-to-br from-green-50 to-emerald-100 rounded-xl shadow-sm">
      <h2 class="text-xl font-bold mb-4 flex items-center gap-2">
        <span class="text-3xl">🔑</span>
        <span>关键特点</span>
      </h2>
      <div class="space-y-3 text-sm">
        <div class="p-3 bg-white rounded-lg flex items-start gap-3">
          <span class="text-2xl">⚡</span>
          <div>
            <div class="font-bold">创建分支很快</div>
            <div class="text-xs opacity-75">只是创建一个指针</div>
          </div>
        </div>
        <div class="p-3 bg-white rounded-lg flex items-start gap-3">
          <span class="text-2xl">🔒</span>
          <div>
            <div class="font-bold">互不影响</div>
            <div class="text-xs opacity-75">新分支修改不影响 main</div>
          </div>
        </div>
        <div class="p-3 bg-white rounded-lg flex items-start gap-3">
          <span class="text-2xl">🔄</span>
          <div>
            <div class="font-bold">随时切换</div>
            <div class="text-xs opacity-75">在不同分支间自由切换</div>
          </div>
        </div>
      </div>
    </div>
  </div>

</div>

---
transition: slide-left
---

# `git branch` - 分支操作

<div class="grid grid-cols-2 gap-5 mt-4">

  <div v-motion :initial="{ y: -50, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-4 bg-gradient-to-br from-blue-50 to-blue-100 rounded-xl shadow-sm">
      <h2 class="text-lg font-bold mb-3 flex items-center gap-2">
        <span class="text-2xl">👀</span>
        <span>查看分支</span>
      </h2>
      <div class="space-y-2">
        <div class="bg-blue-50 border border-blue-300 text-gray-800 p-3 rounded-lg font-mono text-xs">
          <div class="opacity-50"># 查看本地分支</div>
          <div>git branch</div>
        </div>
        <div class="bg-blue-50 border border-blue-300 text-gray-800 p-3 rounded-lg font-mono text-xs">
          <div class="opacity-50"># 查看所有分支(含远程)</div>
          <div>git branch -a</div>
        </div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ y: -50, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-4 bg-gradient-to-br from-green-50 to-emerald-100 rounded-xl shadow-sm">
      <h2 class="text-lg font-bold mb-3 flex items-center gap-2">
        <span class="text-2xl">➕</span>
        <span>创建分支</span>
      </h2>
      <div class="bg-green-50 border border-green-300 text-gray-800 p-3 rounded-lg font-mono text-xs">
        <div class="opacity-50"># 创建新分支</div>
        <div>git branch feat/add-user-auth</div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ y: 50, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-4 bg-gradient-to-br from-red-50 to-orange-50 rounded-xl shadow-sm">
      <h2 class="text-lg font-bold mb-3 flex items-center gap-2">
        <span class="text-2xl">🗑️</span>
        <span>删除分支</span>
      </h2>
      <div class="space-y-2">
        <div class="bg-orange-50 border border-orange-300 text-gray-800 p-3 rounded-lg font-mono text-xs">
          <div class="opacity-50"># 安全删除(已合并)</div>
          <div>git branch -d feat/add-user-auth</div>
        </div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ y: 50, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-4 bg-gradient-to-br from-purple-50 to-pink-50 rounded-xl shadow-sm">
      <h2 class="text-lg font-bold mb-3 flex items-center gap-2">
        <span class="text-2xl">⚠️</span>
        <span>强制删除</span>
      </h2>
      <div class="bg-purple-50 border border-purple-300 text-gray-800 p-3 rounded-lg font-mono text-xs">
        <div class="opacity-50"># 强制删除(未合并)</div>
        <div>git branch -D feat/add-user-auth</div>
      </div>
    </div>
  </div>

</div>

---
transition: fade
---

# `git switch` / `git checkout` - 切换分支

<div v-motion :initial="{ scale: 0.95, opacity: 0 }" :enter="{ scale: 1, opacity: 1, transition: { delay: 800 } }">
  <div class="p-6 bg-gradient-to-br from-purple-50 to-indigo-100 rounded-xl shadow-md mb-4">
    <h2 class="text-2xl font-bold mb-4">⭐ 现代用法(推荐)</h2>
    <div class="grid grid-cols-3 gap-4">
      <div v-motion :initial="{ x: -30, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }" class="p-4 bg-white rounded-lg shadow-sm">
        <div class="font-bold text-sm mb-2">切换分支</div>
        <div class="bg-purple-50 border border-purple-300 text-gray-800 p-2 rounded font-mono text-xs">
          git switch feat/async
        </div>
      </div>
      <div v-motion :initial="{ y: 30, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }" class="p-4 bg-white rounded-lg shadow-sm">
        <div class="font-bold text-sm mb-2">创建并切换</div>
        <div class="bg-purple-50 border border-purple-300 text-gray-800 p-2 rounded font-mono text-xs">
          git switch -c feat/macro
        </div>
      </div>
      <div v-motion :initial="{ x: 30, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }" class="p-4 bg-white rounded-lg shadow-sm">
        <div class="font-bold text-sm mb-2">切回上一个</div>
        <div class="bg-purple-50 border border-purple-300 text-gray-800 p-2 rounded font-mono text-xs">
          git switch -
        </div>
      </div>
    </div>
  </div>
</div>

<div v-motion :initial="{ y: 30, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 900 } }">
  <div class="p-4 bg-gray-50 rounded-lg border-2 border-gray-300 mt-4">
    <h2 class="text-lg font-bold mb-3">📜 传统用法</h2>
    <div class="bg-blue-50 border border-blue-300 text-gray-800 p-3 rounded-lg font-mono text-xs space-y-1">
      <div>git checkout feat/async <span class="opacity-50"># 切换分支</span></div>
      <div>git checkout -b feat/macro <span class="opacity-50"># 创建并切换</span></div>
    </div>
    <div class="mt-2 text-xs opacity-75 flex items-center gap-2">
      <span>💡</span>
      <span>推荐使用 <code class="bg-white px-1 rounded">git switch</code>,语义更清晰</span>
    </div>
  </div>
</div>

---
transition: slide-up
---

# `git merge` - 合并分支

<div class="grid grid-cols-2 gap-6 mt-4">

  <div v-motion :initial="{ x: -50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-5 bg-gradient-to-br from-blue-50 to-cyan-50 rounded-xl shadow-sm">
      <h2 class="text-xl font-bold mb-4">合并步骤</h2>
      <div class="space-y-3">
        <div class="flex items-start gap-3 p-3 bg-white rounded-lg shadow-sm">
          <div class="w-6 h-6 bg-blue-500 text-white rounded-full flex items-center justify-center text-xs font-bold flex-shrink-0">1</div>
          <div>
            <div class="font-bold text-sm">切换到目标分支</div>
            <div class="bg-blue-50 border border-blue-300 text-gray-800 p-2 rounded font-mono text-xs mt-1">
              git switch main
            </div>
          </div>
        </div>
        <div class="flex items-start gap-3 p-3 bg-white rounded-lg shadow-sm">
          <div class="w-6 h-6 bg-green-500 text-white rounded-full flex items-center justify-center text-xs font-bold flex-shrink-0">2</div>
          <div>
            <div class="font-bold text-sm">合并分支</div>
            <div class="bg-blue-50 border border-blue-300 text-gray-800 p-2 rounded font-mono text-xs mt-1">
              git merge feat/async
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ x: 50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-5 bg-gradient-to-br from-purple-50 to-pink-50 rounded-xl shadow-sm">
      <h2 class="text-xl font-bold mb-4">Git 会自动合并</h2>
      <div class="space-y-3 text-sm">
        <div class="p-3 bg-green-100 rounded-lg border-l-4 border-green-500">
          <div class="font-bold">✨ 简单合并(Fast-forward)</div>
          <div class="text-xs opacity-75 mt-1">main 没新提交,直接加上 feature 的提交</div>
        </div>
        <div class="p-3 bg-blue-100 rounded-lg border-l-4 border-blue-500">
          <div class="font-bold">🔄 复杂合并(Merge commit)</div>
          <div class="text-xs opacity-75 mt-1">两边都有新提交,Git 创建一个"合并提交"</div>
        </div>
      </div>
    </div>
  </div>

</div>

<div v-motion :initial="{ y: 30, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }" class="mt-6 p-2 bg-blue-50 rounded text-sm">
  💡 大多数情况 Git 会自动处理,你只需执行 <code>git merge</code>
</div>

---
transition: fade
---

# 合并冲突 - 新手最怕的问题

<div class="grid grid-cols-2 gap-6 mt-4">

  <div v-motion :initial="{ x: -50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-5 bg-gradient-to-br from-red-50 to-orange-50 rounded-xl shadow-sm">
      <h2 class="text-xl font-bold mb-4">什么时候会冲突?</h2>
      <p class="text-sm mb-3">两个分支修改了<span class="font-bold text-red-600">同一个文件的同一行</span>,Git 不知道保留哪个</p>
      <div class="bg-orange-50 border border-orange-300 text-gray-800 p-4 rounded-lg font-mono text-xs">
        <div class="text-purple-600 font-bold">&lt;&lt;&lt;&lt;&lt;&lt;&lt; HEAD</div>
        <div class="text-blue-600">let count = 10; <span class="opacity-50">// 你的修改</span></div>
        <div class="text-orange-600 font-bold">=======</div>
        <div class="text-green-600">let count = 20; <span class="opacity-50">// 他人的修改</span></div>
        <div class="text-purple-600 font-bold">&gt;&gt;&gt;&gt;&gt;&gt;&gt; feat/update</div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ x: 50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-5 bg-gradient-to-br from-green-50 to-emerald-100 rounded-xl shadow-sm">
      <h2 class="text-xl font-bold mb-4">解决步骤</h2>
      <div class="space-y-2 text-sm">
        <div class="flex items-start gap-3 p-3 bg-white rounded-lg shadow-sm">
          <div class="w-6 h-6 bg-blue-500 text-white rounded-full flex items-center justify-center text-xs font-bold flex-shrink-0">1</div>
          <div>
            <div class="font-bold">打开冲突文件</div>
            <div class="text-xs opacity-75">找到 &lt;&lt;&lt;&lt;&lt;&lt;&lt; HEAD 标记</div>
          </div>
        </div>
        <div class="flex items-start gap-3 p-3 bg-white rounded-lg shadow-sm">
          <div class="w-6 h-6 bg-green-500 text-white rounded-full flex items-center justify-center text-xs font-bold flex-shrink-0">2</div>
          <div>
            <div class="font-bold">手动编辑代码</div>
            <div class="text-xs opacity-75">删除标记,保留需要的内容</div>
          </div>
        </div>
        <div class="flex items-start gap-3 p-3 bg-white rounded-lg shadow-sm">
          <div class="w-6 h-6 bg-purple-500 text-white rounded-full flex items-center justify-center text-xs font-bold flex-shrink-0">3</div>
          <div>
            <div class="font-bold">标记为已解决</div>
            <div class="bg-green-50 border border-green-300 text-gray-800 p-1 rounded font-mono text-xs mt-1">
              git add src/main.rs
            </div>
            <div class="bg-green-50 border border-green-300 text-gray-800 p-1 rounded font-mono text-xs mt-1">
              git commit
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

</div>

<div v-motion :initial="{ y: 30, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }" class="mt-6 p-4 bg-yellow-50 rounded-xl border-l-4 border-yellow-400 flex items-start gap-3">
  <span class="text-2xl">💡</span>
  <div>
    <div class="font-bold text-lg">VSCode 提示</div>
    <div class="text-sm opacity-75">冲突文件会高亮显示,并提供<span class="font-bold text-yellow-600">"接受当前更改"/"接受传入更改"</span>按钮,点击即可快速解决</div>
  </div>
</div>

---
transition: slide-left
---

# `git stash` - 临时保存工作

<div v-motion :initial="{ y: -20, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 200 } }" class="mb-5">
  <div class="p-4 bg-gradient-to-r from-yellow-50 to-orange-50 rounded-xl border-2 border-orange-300">
    <h3 class="text-lg font-bold mb-2">💡 使用场景</h3>
    <div class="text-sm">代码写到一半,突然需要切换分支修复紧急 Bug,但当前改动还不想提交</div>
    <div class="flex items-center gap-3 mt-3 text-xs">
      <div class="px-3 py-1 bg-red-100 rounded">❌ 不能直接切换(会丢失或冲突)</div>
      <div class="px-3 py-1 bg-green-100 rounded">✅ 用 stash 临时存起来</div>
    </div>
  </div>
</div>

<div class="grid grid-cols-2 gap-5">

  <div v-motion :initial="{ x: -50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-4 bg-gradient-to-br from-blue-50 to-cyan-50 rounded-xl shadow-sm">
      <h2 class="text-lg font-bold mb-3">基本用法</h2>
      <div class="bg-blue-50 border border-blue-300 text-gray-800 p-3 rounded-lg font-mono text-xs space-y-1">
        <div><span class="opacity-50"># 1. 储藏当前工作</span></div>
        <div>git stash</div>
        <div class="mt-1"><span class="opacity-50"># 2. 切换分支修 Bug</span></div>
        <div>git switch main</div>
        <div class="opacity-50"># 修复 Bug...</div>
        <div class="mt-1"><span class="opacity-50"># 3. 切回原分支</span></div>
        <div>git switch feat/feature</div>
        <div class="mt-1"><span class="opacity-50"># 4. 恢复工作</span></div>
        <div>git stash pop</div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ x: 50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-4 bg-gradient-to-br from-purple-50 to-pink-50 rounded-xl shadow-sm">
      <h2 class="text-lg font-bold mb-3">常用命令</h2>
      <div class="space-y-2">
        <div class="p-2 bg-white rounded-lg shadow-sm">
          <div class="font-bold text-xs mb-1">查看所有 stash</div>
          <div class="bg-purple-50 border border-purple-300 text-gray-800 p-2 rounded font-mono text-xs">
            git stash list
          </div>
        </div>
        <div class="p-2 bg-white rounded-lg shadow-sm">
          <div class="font-bold text-xs mb-1">恢复但不删除</div>
          <div class="bg-purple-50 border border-purple-300 text-gray-800 p-2 rounded font-mono text-xs">
            git stash apply stash@{0}
          </div>
        </div>
        <div class="p-2 bg-white rounded-lg shadow-sm">
          <div class="font-bold text-xs mb-1">删除 stash</div>
          <div class="bg-purple-50 border border-purple-300 text-gray-800 p-2 rounded font-mono text-xs">
            git stash drop stash@{0}
          </div>
        </div>
      </div>
    </div>
  </div>

</div>

---
layout: center
class: text-center
transition: slide-down
---

<div class="text-center">
  <div class="text-6xl mb-6">⏮️</div>
  <h1 class="text-4xl font-bold text-orange-600 mb-3">代码"后悔药"</h1>
  <p class="text-xl opacity-60">撤销操作</p>
</div>

---
transition: slide-up
---

# `git revert`：安全地撤销

`revert` 用于创建一个**新的提交**，其内容与你想要撤销的提交**完全相反**。

- **优点**：**不修改项目历史**。它是在历史之上“追加”一次撤销操作，因此对于已经推送到远程的、与团队共享的分支来说，这是**唯一安全**的撤销方式。

```bash
# 假设 5d7a5b 是一个错误的提交
# 这会创建一个新的提交，内容是 5d7a5b 的反向操作
git revert 5d7a5b
```
<div class="flex items-center justify-center mt-8">
    <img src="/git-revert-diagram.svg" alt="Git Revert 示意图" class="w-full max-w-3xl" />
  </div>
---
transition: slide-up
---

# `git reset`：强大的历史改写工具

<div v-motion :initial="{ scale: 0.95, opacity: 0 }" :enter="{ scale: 1, opacity: 1, transition: { delay: 800 } }">
  <div class="p-5 bg-gradient-to-br from-purple-50 to-indigo-100 rounded-xl shadow-md mb-4">
    <h2 class="text-xl font-bold mb-3 flex items-center gap-2">
      <span class="text-3xl">⚙️</span>
      <span>什么是 reset?</span>
    </h2>
    <p class="text-sm">移动当前分支的 HEAD 指针到指定提交,并根据模式更新暂存区和工作区。<span class="font-bold text-red-600">它会修改历史!</span></p>
  </div>
</div>

<div class="grid grid-cols-3 gap-4 mt-4">
  <div v-motion :initial="{ y: 50, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-4 bg-gradient-to-br from-blue-50 to-blue-100 rounded-xl shadow-sm">
      <div class="text-1xl mb-2">💫--soft</div>
      <div class="text-xs space-y-2">
        <div class="p-2 bg-white rounded">只移动 HEAD 指针</div>
        <div class="p-2 bg-green-100 rounded">✓ 暂存区不变</div>
        <div class="p-2 bg-green-100 rounded">✓ 工作区不变</div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ y: 50, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-4 bg-gradient-to-br from-yellow-50 to-yellow-100 rounded-xl shadow-sm">
      <div class="text-1xl mb-2">⚡--mixed(默认)</div>
      <div class="text-xs space-y-2">
        <div class="p-2 bg-white rounded">移动 HEAD</div>
        <div class="p-2 bg-red-100 rounded">✗ 重置暂存区</div>
        <div class="p-2 bg-green-100 rounded">✓ 工作区不变</div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ y: 50, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-4 bg-gradient-to-br from-red-50 to-red-100 rounded-xl shadow-sm">
      <div class="text-1xl mb-2">💥--hard</div>
      <div class="text-xs space-y-2">
        <div class="p-2 bg-white rounded">移动 HEAD</div>
        <div class="p-2 bg-red-100 rounded">✗ 重置暂存区</div>
        <div class="p-2 bg-red-100 rounded">✗ 丢弃工作区</div>
      </div>
    </div>
  </div>

</div>

<div v-motion :initial="{ y: 30, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 900 } }" class="mt-6 p-5 bg-red-100 rounded-xl border-2 border-red-400 flex items-start gap-3">
  <span class="text-4xl">⚠️</span>
  <div>
    <div class="font-bold text-xl text-red-600">警告</div>
    <div class="text-sm mt-1"><span class="font-bold">绝对不要</span> reset 已经被推送到<span class="font-bold text-red-600">远程共享分支</span>的提交!</div>
  </div>
</div>


---
transition: slide-right
---

# Commit Message 规范

<div v-motion :initial="{ scale: 0.95, opacity: 0 }" :enter="{ scale: 1, opacity: 1, transition: { delay: 800 } }">
  <div class="p-5 bg-gradient-to-br from-purple-50 to-indigo-100 rounded-xl shadow-md mb-4">
    <h2 class="text-2xl font-bold mb-3 flex items-center gap-2">
      <span class="text-3xl">📝</span>
      <span>约定式提交（Conventional Commits）</span>
    </h2>
    <div class="bg-blue-50 border border-blue-300 text-gray-800 p-4 rounded-lg font-mono text-sm mb-3">
      <span class="font-bold text-blue-600">&lt;type&gt;</span><span class="font-bold text-purple-600">(&lt;scope&gt;)</span>: <span class="font-bold text-yellow-600">&lt;subject&gt;</span>
      <div class="mt-2 text-xs opacity-75">
        <div>&lt;空行&gt;</div>
        <div>&lt;body&gt;</div>
        <div>&lt;空行&gt;</div>
        <div>&lt;footer&gt;</div>
      </div>
    </div>
    <div class="text-xs opacity-75">
      <span class="font-bold">type</span>: 必填，提交类型 | 
      <span class="font-bold">scope</span>: 可选，影响范围 | 
      <span class="font-bold">subject</span>: 必填，简短描述
    </div>
  </div>
</div>

---
transition: fade
---

# 常用 Type 类型详解

<div class="grid grid-cols-2 gap-3 mt-3">
  <div v-motion :initial="{ y: 30, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="space-y-2">
      <div class="p-2 bg-green-50 rounded-lg border-l-4 border-green-500">
        <div class="flex items-center gap-2 mb-1">
          <code class="font-bold text-green-700 text-xs">feat</code>
          <span class="text-xs bg-green-200 px-2 py-0.5 rounded">新功能</span>
        </div>
        <div class="text-xs opacity-75">添加新功能、新特性</div>
        <div class="text-xs font-mono bg-green-50 border border-green-300 text-gray-800 p-1.5 rounded mt-1">
          feat: 添加用户登录功能
        </div>
      </div>
      <div class="p-2 bg-red-50 rounded-lg border-l-4 border-red-500">
        <div class="flex items-center gap-2 mb-1">
          <code class="font-bold text-red-700 text-xs">fix</code>
          <span class="text-xs bg-red-200 px-2 py-0.5 rounded">Bug 修复</span>
        </div>
        <div class="text-xs opacity-75">修复缺陷、错误</div>
        <div class="text-xs font-mono bg-red-50 border border-red-300 text-gray-800 p-1.5 rounded mt-1">
          fix: 修复登录验证失败问题
        </div>
      </div>
      <div class="p-2 bg-blue-50 rounded-lg border-l-4 border-blue-500">
        <div class="flex items-center gap-2 mb-1">
          <code class="font-bold text-blue-700 text-xs">docs</code>
          <span class="text-xs bg-blue-200 px-2 py-0.5 rounded">文档</span>
        </div>
        <div class="text-xs opacity-75">仅修改文档</div>
        <div class="text-xs font-mono bg-blue-50 border border-blue-300 text-gray-800 p-1.5 rounded mt-1">
          docs: 更新 API 使用文档
        </div>
      </div>
      <div class="p-2 bg-purple-50 rounded-lg border-l-4 border-purple-500">
        <div class="flex items-center gap-2 mb-1">
          <code class="font-bold text-purple-700 text-xs">style</code>
          <span class="text-xs bg-purple-200 px-2 py-0.5 rounded">代码格式</span>
        </div>
        <div class="text-xs opacity-75">不影响代码功能的改动</div>
        <div class="text-xs font-mono bg-purple-50 border border-purple-300 text-gray-800 p-1.5 rounded mt-1">
          style: 格式化代码缩进
        </div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ y: 30, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="space-y-2">
      <div class="p-2 bg-yellow-50 rounded-lg border-l-4 border-yellow-500">
        <div class="flex items-center gap-2 mb-1">
          <code class="font-bold text-yellow-700 text-xs">refactor</code>
          <span class="text-xs bg-yellow-200 px-2 py-0.5 rounded">重构</span>
        </div>
        <div class="text-xs opacity-75">既不是新功能也不是修复</div>
        <div class="text-xs font-mono bg-yellow-50 border border-yellow-300 text-gray-800 p-1.5 rounded mt-1">
          refactor: 重构用户认证模块
        </div>
      </div>
      <div class="p-2 bg-orange-50 rounded-lg border-l-4 border-orange-500">
        <div class="flex items-center gap-2 mb-1">
          <code class="font-bold text-orange-700 text-xs">perf</code>
          <span class="text-xs bg-orange-200 px-2 py-0.5 rounded">性能优化</span>
        </div>
        <div class="text-xs opacity-75">提升性能的代码改动</div>
        <div class="text-xs font-mono bg-orange-50 border border-orange-300 text-gray-800 p-1.5 rounded mt-1">
          perf: 优化数据库查询速度
        </div>
      </div>
      <div class="p-2 bg-pink-50 rounded-lg border-l-4 border-pink-500">
        <div class="flex items-center gap-2 mb-1">
          <code class="font-bold text-pink-700 text-xs">test</code>
          <span class="text-xs bg-pink-200 px-2 py-0.5 rounded">测试</span>
        </div>
        <div class="text-xs opacity-75">添加或修改测试代码</div>
        <div class="text-xs font-mono bg-pink-50 border border-pink-300 text-gray-800 p-1.5 rounded mt-1">
          test: 添加用户注册单元测试
        </div>
      </div>
      <div class="p-2 bg-gray-50 rounded-lg border-l-4 border-gray-500">
        <div class="flex items-center gap-2 mb-1">
          <code class="font-bold text-gray-700 text-xs">chore</code>
          <span class="text-xs bg-gray-200 px-2 py-0.5 rounded">杂项</span>
        </div>
        <div class="text-xs opacity-75">构建过程、辅助工具的变动</div>
        <div class="text-xs font-mono bg-gray-100 border border-gray-300 text-gray-800 p-1.5 rounded mt-1">
          chore: 更新依赖包版本
        </div>
      </div>
    </div>
  </div>
</div>

---
transition: slide-up
---

# 好的 vs 坏的 Commit Message

<div class="grid grid-cols-2 gap-5 mt-3">
  <div v-motion :initial="{ x: -50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-4 bg-gradient-to-br from-red-50 to-red-100 rounded-xl shadow-sm">
      <h2 class="text-lg font-bold mb-3">❌ 反面教材</h2>
      <div class="space-y-2 text-sm">
        <div class="bg-red-50 border border-red-300 text-red-700 p-2 rounded-lg font-mono text-xs">
          update
        </div>
        <div class="text-xs opacity-75 bg-white p-1.5 rounded">❌ 太模糊,不知道改了什么</div>
        <div class="bg-red-50 border border-red-300 text-red-700 p-2 rounded-lg font-mono text-xs">
          fix bug
        </div>
        <div class="text-xs opacity-75 bg-white p-1.5 rounded">❌ 修了什么 Bug?</div>
        <div class="bg-red-50 border border-red-300 text-red-700 p-2 rounded-lg font-mono text-xs">
          修改了一些代码
        </div>
        <div class="text-xs opacity-75 bg-white p-1.5 rounded">❌ 完全没有信息量</div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ x: 50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-4 bg-gradient-to-br from-green-50 to-emerald-100 rounded-xl shadow-sm">
      <h2 class="text-lg font-bold mb-3">✅ 正面示例</h2>
      <div class="space-y-2 text-sm">
        <div class="bg-green-50 border border-green-300 text-gray-800 p-2 rounded-lg font-mono text-xs">
          feat: 添加邮箱验证功能
        </div>
        <div class="text-xs opacity-75 bg-white p-1.5 rounded">✅ 清楚说明了新增的功能</div>
        <div class="bg-green-50 border border-green-300 text-gray-800 p-2 rounded-lg font-mono text-xs">
          fix: 修复用户头像上传失败
        </div>
        <div class="text-xs opacity-75 bg-white p-1.5 rounded">✅ 具体说明修复了什么</div>
        <div class="bg-green-50 border border-green-300 text-gray-800 p-2 rounded-lg font-mono text-xs">
          perf(api): 优化列表查询性能
        </div>
        <div class="text-xs opacity-75 bg-white p-1.5 rounded">✅ 带 scope,更精确</div>
      </div>
    </div>
  </div>
</div>

---
transition: fade
---

# Commit Message 最佳实践

<div class="grid grid-cols-2 gap-4 mt-3">
  <div v-motion :initial="{ y: 30, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-4 bg-gradient-to-br from-blue-50 to-cyan-50 rounded-xl shadow-sm">
      <h2 class="text-lg font-bold mb-2 flex items-center gap-2">
        <span class="text-2xl">📋</span>
        <span>编写规则</span>
      </h2>
      <div class="space-y-2 text-sm">
        <div class="flex items-center gap-2 p-2 bg-white rounded-lg">
          <div class="text-lg">1️⃣</div>
          <div>
            <span class="font-bold">使用动词开头</span>
            <span class="text-xs opacity-75 ml-1">添加、修复...</span>
          </div>
        </div>
        <div class="flex items-center gap-2 p-2 bg-white rounded-lg">
          <div class="text-lg">2️⃣</div>
          <div>
            <span class="font-bold">使用现在时态</span>
            <span class="text-xs opacity-75 ml-1">"添加" 不是 "添加了"</span>
          </div>
        </div>
        <div class="flex items-center gap-2 p-2 bg-white rounded-lg">
          <div class="text-lg">3️⃣</div>
          <div>
            <span class="font-bold">首字母小写</span>
            <span class="text-xs opacity-75 ml-1">feat: 而非 Feat:</span>
          </div>
        </div>
        <div class="flex items-center gap-2 p-2 bg-white rounded-lg">
          <div class="text-lg">4️⃣</div>
          <div>
            <span class="font-bold">不用句号结尾</span>
            <span class="text-xs opacity-75 ml-1">保持简洁</span>
          </div>
        </div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ y: 30, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-4 bg-gradient-to-br from-purple-50 to-pink-50 rounded-xl shadow-sm">
      <h2 class="text-lg font-bold mb-2 flex items-center gap-2">
        <span class="text-2xl">💡</span>
        <span>进阶技巧</span>
      </h2>
      <div class="space-y-2 text-sm">
        <div class="p-2 bg-white rounded-lg">
          <div class="font-bold mb-1 text-sm">带 scope 更精确</div>
          <div class="bg-blue-50 border border-blue-200 text-gray-800 px-2 py-1 rounded font-mono text-xs">
            feat(auth): 添加 JWT 认证
          </div>
        </div>
        <div class="p-2 bg-white rounded-lg">
          <div class="font-bold mb-1 text-sm">关联 Issue</div>
          <div class="bg-green-50 border border-green-200 text-gray-800 px-2 py-1 rounded font-mono text-xs">
            fix: 修复登录问题 #123
          </div>
        </div>
        <div class="p-2 bg-white rounded-lg">
          <div class="font-bold mb-1 text-sm">破坏性变更</div>
          <div class="bg-orange-50 border border-orange-200 text-gray-800 px-2 py-1 rounded font-mono text-xs">
            feat!: 重构 API 接口<br/>
            <span class="text-xs opacity-75">BREAKING CHANGE: 移除旧版</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<div v-motion :initial="{ y: 30, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 1000 } }" class="mt-4 p-3 bg-yellow-50 rounded-xl border-l-4 border-yellow-400 flex items-start gap-3">
  <span class="text-3xl">🎯</span>
  <div>
    <div class="font-bold">记住核心原则</div>
    <div class="text-sm opacity-75">一个月后的你，或者你的队友，应该能通过 commit message <span class="font-bold text-yellow-600">立刻明白这次改动做了什么</span></div>
  </div>
</div>

---
transition: side-up
---

# 常见错误与解决方案

<div v-motion :initial="{ scale: 0.95, opacity: 0 }" :enter="{ scale: 1, opacity: 1, transition: { delay: 800 } }" class="mt-2">
  <div class="space-y-2">
    <div v-motion :initial="{ x: -30, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }" class="grid grid-cols-2 gap-3 p-3 bg-red-50 rounded-xl">
      <div>
        <div class="flex items-center gap-2">
          <span class="text-2xl">🔐</span>
          <div class="font-bold text-sm">不小心提交了密码</div>
        </div>
        <div class="text-xs opacity-75 mt-0.5">敏感信息不小心 commit 了</div>
      </div>
      <div>
        <div class="bg-red-50 border border-red-300 text-gray-800 p-1.5 rounded font-mono text-xs">
          <div class="text-red-600 font-bold">⚠️ 立即改密码!</div>
          <div class="mt-0.5">git revert <span class="text-red-600">&lt;commit&gt;</span></div>
        </div>
        <div class="text-xs opacity-75 mt-0.5">创建新提交来撤销</div>
      </div>
    </div>
    <div v-motion :initial="{ x: -30, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }" class="grid grid-cols-2 gap-3 p-3 bg-orange-50 rounded-xl">
      <div>
        <div class="flex items-center gap-2">
          <span class="text-2xl">✏️</span>
          <div class="font-bold text-sm">提交信息写错了</div>
        </div>
        <div class="text-xs opacity-75 mt-0.5">刚 commit 完，发现消息写错了</div>
      </div>
      <div>
        <div class="bg-orange-50 border border-orange-300 text-gray-800 p-1.5 rounded font-mono text-xs">
          git commit --amend -m <span class="text-orange-600">"正确信息"</span>
        </div>
        <div class="text-xs opacity-75 mt-0.5">修改最后一次提交（还没 push）</div>
      </div>
    </div>
    <div v-motion :initial="{ x: -30, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }" class="grid grid-cols-2 gap-3 p-3 bg-yellow-50 rounded-xl">
      <div>
        <div class="flex items-center gap-2">
          <span class="text-2xl">📝</span>
          <div class="font-bold text-sm">add 错文件了</div>
        </div>
        <div class="text-xs opacity-75 mt-0.5">不小心 git add 了不该提交的文件</div>
      </div>
      <div>
        <div class="bg-yellow-50 border border-yellow-300 text-gray-800 p-1.5 rounded font-mono text-xs">
          git restore --staged <span class="text-orange-600">文件名</span>
        </div>
        <div class="text-xs opacity-75 mt-0.5">从暂存区移除，但保留修改</div>
      </div>
    </div>
    <div v-motion :initial="{ x: -30, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 900 } }" class="grid grid-cols-2 gap-3 p-3 bg-blue-50 rounded-xl">
      <div>
        <div class="flex items-center gap-2">
          <span class="text-2xl">💥</span>
          <div class="font-bold text-sm">工作区文件改坏了</div>
        </div>
        <div class="text-xs opacity-75 mt-0.5">还没 commit，想恢复到上次提交</div>
      </div>
      <div>
        <div class="bg-blue-50 border border-blue-300 text-gray-800 p-1.5 rounded font-mono text-xs">
          git restore <span class="text-blue-600">文件名</span>
        </div>
        <div class="text-xs opacity-75 mt-0.5">⚠️ 会丢失未提交的修改！</div>
      </div>
    </div>
  </div>
</div>

<div v-motion :initial="{ y: 10, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 1100 } }" class="mt-3 p-3 bg-blue-50 rounded-xl border-l-4 border-blue-400 flex items-start gap-2">
  <span class="text-3xl">💡</span>
  <div class="text-sm">
    <span class="font-bold">记住</span>: Git 很难把代码彻底删除，<span class="font-bold text-blue-600">大胆尝试</span>！遇到问题先 <code class="bg-white px-2 py-1 rounded">git status</code>
  </div>
</div>


---
transition: fade
---

# `git tag`：标记你的版本

<div v-motion :initial="{ y: -20, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 200 } }" class="mt-4">
  <div class="p-5 bg-gradient-to-br from-purple-50 to-indigo-100 rounded-xl shadow-sm">
    <h2 class="text-xl font-bold mb-3 flex items-center gap-2">
      <span class="text-xl">🏷️</span>
      <span>什么是 tag?</span>
    </h2>
    <p class="text-sm mb-3">为特定 commit 创建<span class="font-bold text-purple-600">永久标记</span>,通常用于<span class="font-bold">版本发布</span></p>
    <div class="grid grid-cols-3 gap-3 text-sm">
      <div class="flex items-center gap-2">
        <span class="text-green-500">✓</span>
        <span>标记重要里程碑</span>
      </div>
      <div class="flex items-center gap-2">
        <span class="text-green-500">✓</span>
        <span>方便版本回溯</span>
      </div>
      <div class="flex items-center gap-2">
        <span class="text-green-500">✓</span>
        <span>清晰的版本历史</span>
      </div>
    </div>
  </div>
</div>

<div v-motion :initial="{ y: 20, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 400 } }" class="mt-5">
  <div class="p-5 bg-gradient-to-br from-blue-50 to-cyan-50 rounded-xl shadow-sm">
    <h2 class="text-xl font-bold mb-4 flex items-center gap-2">
      <span class="text-xl">💻</span>
      <span>常用命令</span>
    </h2>
    <div class="grid grid-cols-3 gap-4 text-sm">
      <div>
        <div class="font-bold mb-2">轻量标签</div>
        <div class="bg-blue-50 border border-blue-300 text-gray-800 p-2 rounded font-mono text-xs">
          git tag v1.0.0
        </div>
      </div>
      <div>
        <div class="font-bold mb-2">附注标签 (推荐)</div>
        <div class="bg-blue-50 border border-blue-300 text-gray-800 p-2 rounded font-mono text-xs">
          git tag -a v1.0.0 -m "Release"
        </div>
      </div>
      <div>
        <div class="font-bold mb-2">推送标签</div>
        <div class="bg-blue-50 border border-blue-300 text-gray-800 p-2 rounded font-mono text-xs">
          git push origin --tags
        </div>
      </div>
    </div>
  </div>
</div>

---
layout: center
class: text-center
transition: slide-down
---

<div class="text-center">
  <div class="text-6xl mb-6">🌐</div>
  <h1 class="text-4xl font-bold text-purple-600 mb-3">远程协作 · GitHub</h1>
  <p class="text-xl opacity-60">将代码托管到云端,与团队协作</p>
</div>

---
transition: fade-out
---

# 理解远程仓库 (Remote)

<div class="grid grid-cols-2 gap-6 mt-4">

  <div v-motion :initial="{ x: -50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 200 } }">
    <div class="p-5 bg-gradient-to-br from-blue-50 to-cyan-50 rounded-xl shadow-sm">
      <h2 class="text-xl font-bold mb-3 flex items-center gap-2">
        <span class="text-3xl">☁️</span>
        <span>什么是远程仓库?</span>
      </h2>
      <div class="text-sm space-y-3">
        <p>远程仓库是托管在<span class="font-bold text-blue-600">网络服务器</span>上的你的项目版本</p>
        <div class="p-3 bg-white rounded-lg">
          <code class="text-blue-600">origin</code> 是 Git 在你 <code class="text-xs bg-gray-100 px-1 rounded">clone</code> 项目时创建的远程仓库<span class="font-bold">默认名称</span>
        </div>
        <div>
          <div class="font-bold mb-2">常见的托管平台:</div>
          <div class="space-y-2 text-xs">
            <div class="flex items-center gap-2 p-2 bg-white rounded">
              <span><span class="font-bold">GitHub</span> - 最流行的开源平台</span>
            </div>
            <div class="flex items-center gap-2 p-2 bg-white rounded">
              <span><span class="font-bold">GitLab</span> - 支持私有部署</span>
            </div>
            <div class="flex items-center gap-2 p-2 bg-white rounded">
              <span><span class="font-bold">Gitee</span> - 国内访问快</span>
            </div>
            <div class="flex items-center gap-2 p-2 bg-white rounded">
              <span class="font-bold">还可以有很多,我们以github为例</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ x: 50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-5 bg-gradient-to-br from-green-50 to-emerald-50 rounded-xl shadow-sm">
      <h2 class="text-xl font-bold mb-3 flex items-center gap-2">
        <span class="text-3xl">⚙️</span>
        <span>常用命令</span>
      </h2>
      <div class="text-sm space-y-2">
        <div class="p-2 bg-white rounded border-l-4 border-blue-400">
          <code class="text-xs">git remote -v</code>
          <div class="text-xs opacity-75 mt-1">查看所有远程仓库</div>
        </div>
        <div class="p-2 bg-white rounded border-l-4 border-green-400">
          <code class="text-xs">git remote add &lt;name&gt; &lt;url&gt;</code>
          <div class="text-xs opacity-75 mt-1">添加新的远程仓库</div>
        </div>
        <div class="p-2 bg-white rounded border-l-4 border-red-400">
          <code class="text-xs">git remote remove &lt;name&gt;</code>
          <div class="text-xs opacity-75 mt-1">移除远程仓库</div>
        </div>
      </div>
    </div>
  </div>

</div>

---
transition: slide-left
---

# `git clone` - 克隆远程仓库

<div class="grid grid-cols-2 gap-6 mt-4">

  <div v-motion :initial="{ x: -50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 200 } }">
    <div class="p-4 bg-gradient-to-br from-blue-50 to-cyan-50 rounded-xl shadow-sm">
      <h2 class="text-xl font-bold mb-3 flex items-center gap-2">
        <span class="text-3xl">📦</span>
        <span>克隆仓库</span>
      </h2>
      <div class="text-sm space-y-3">
        <p><code class="bg-white px-2 py-1 rounded border">git clone</code> 会完整复制远程仓库到本地</p>
        <div class="bg-gray-50 border border-gray-300 text-gray-800 p-3 rounded font-mono text-xs">
          <div class="opacity-50"># 克隆 GitHub 仓库</div>
          <div>git clone https://github.com/</div>
          <div class="ml-4">username/repo.git</div>
        </div>
        <div class="p-3 bg-green-50 rounded border-l-4 border-green-400">
          <div class="font-bold text-green-600">✅ 自动完成</div>
          <div class="text-xs space-y-1 mt-1">
            <div>• 下载所有文件和历史记录</div>
            <div>• 设置 origin 远程仓库</div>
            <div>• 切换到默认分支</div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ x: 50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-4 bg-gradient-to-br from-purple-50 to-pink-50 rounded-xl shadow-sm">
      <h2 class="text-xl font-bold mb-3 flex items-center gap-2">
        <span class="text-3xl">🔐</span>
        <span>HTTPS vs SSH</span>
      </h2>
      <div class="text-sm space-y-3">
        <div class="p-3 bg-white rounded-lg border-l-4 border-blue-400">
          <div class="font-bold">HTTPS (推荐新手)</div>
          <code class="text-xs">https://github.com/user/repo.git</code>
          <div class="text-xs opacity-75 mt-1">• 简单易用,需要输入密码</div>
        </div>
        <div class="p-3 bg-white rounded-lg border-l-4 border-green-400">
          <div class="font-bold">SSH (更安全)</div>
          <code class="text-xs">git@github.com:user/repo.git</code>
          <div class="text-xs opacity-75 mt-1">• 需要配置密钥,免密推送</div>
        </div>
        <div class="p-2 bg-yellow-50 rounded text-xs">
          <span class="font-bold">💡 提示:</span> 两种方式功能完全相同
        </div>
      </div>
    </div>
  </div>

</div>

---
transition: slide-up
---

# `git fetch` vs `git pull`

<div class="grid grid-cols-2 gap-6 mt-4">

  <div v-motion :initial="{ x: -50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 200 } }">
    <div class="p-4 bg-gradient-to-br from-yellow-50 to-orange-50 rounded-xl shadow-sm">
      <h2 class="text-xl font-bold mb-3 flex items-center gap-2">
        <span class="text-3xl">📥</span>
        <code class="text-orange-600">git fetch</code>
      </h2>
      <div class="text-sm space-y-3">
        <p><span class="font-bold">只下载</span>远程的更新,<span class="font-bold text-red-600">不合并</span>到当前分支</p>
        <div class="bg-gray-50 border border-gray-300 text-gray-800 p-3 rounded font-mono text-xs">
          <div class="opacity-50"># 获取远程更新</div>
          <div>git fetch origin</div>
        </div>
        <div class="p-3 bg-blue-50 rounded border-l-4 border-blue-400">
          <div class="font-bold text-blue-600">✅ 安全操作</div>
          <div class="text-xs mt-1">先看看远程有什么变化,再决定是否合并</div>
        </div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ x: 50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-4 bg-gradient-to-br from-blue-50 to-cyan-50 rounded-xl shadow-sm">
      <h2 class="text-xl font-bold mb-3 flex items-center gap-2">
        <span class="text-3xl">⬇️</span>
        <code class="text-blue-600">git pull</code>
      </h2>
      <div class="text-sm space-y-3">
        <p><span class="font-bold">下载并自动合并</span>远程更新到当前分支</p>
        <div class="bg-gray-50 border border-gray-300 text-gray-800 p-3 rounded font-mono text-xs">
          <div class="opacity-50"># 相当于 fetch + merge</div>
          <div>git pull origin main</div>
        </div>
        <div class="p-3 bg-yellow-50 rounded border-l-4 border-yellow-400">
          <div class="font-bold text-yellow-600">⚠️ 注意</div>
          <div class="text-xs mt-1">可能会产生合并冲突</div>
        </div>
      </div>
    </div>
  </div>

</div>

<div v-motion :initial="{ y: 30, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 1000 } }" class="mt-4">
  <div class="p-3 bg-gradient-to-r from-purple-50 to-indigo-50 rounded-lg border-2 border-purple-300 text-center">
    <div class="text-sm">
      <span class="font-bold">💡 推荐:</span> 开始工作前先 <code class="bg-white px-2 py-1 rounded">git pull</code>,避免冲突
    </div>
  </div>
</div>

---
transition: slide-up
---

# `git push` - 推送到远程

<div class="grid grid-cols-2 gap-6 mt-4">

  <div v-motion :initial="{ y: 50, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-4 bg-gradient-to-br from-blue-50 to-blue-100 rounded-xl shadow-sm">
      <h2 class="text-xl font-bold mb-3 flex items-center gap-2">
        <span class="text-3xl">⬆️</span>
        <span>基本用法</span>
      </h2>
      <div class="text-sm space-y-3">
        <p>将本地提交<span class="font-bold">推送到远程仓库</span></p>
        <div class="bg-gray-50 border border-gray-300 text-gray-800 p-3 rounded font-mono text-xs">
          <div class="opacity-50"># 推送到远程 main 分支</div>
          <div>git push origin main</div>
          <div class="mt-2 opacity-50"># 首次推送,设置上游</div>
          <div>git push -u origin main</div>
        </div>
        <div class="p-3 bg-green-50 rounded border-l-4 border-green-400">
          <div class="font-bold text-green-600">✅ 最佳实践</div>
          <div class="text-xs mt-1">完成功能后及时 push,与团队共享</div>
        </div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ y: 50, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-4 bg-gradient-to-br from-red-50 to-pink-50 rounded-xl shadow-sm">
      <h2 class="text-xl font-bold mb-3 flex items-center gap-2">
        <span class="text-3xl">⚠️</span>
        <span>常见问题</span>
      </h2>
      <div class="text-sm space-y-2">
        <div class="p-2 bg-white rounded border-l-4 border-red-400">
          <div class="font-bold text-red-600">push 被拒绝</div>
          <div class="text-xs mt-1 opacity-75">原因:远程有新提交</div>
          <div class="text-xs mt-1 font-mono bg-gray-50 p-1 rounded">先 git pull 再 push</div>
        </div>
        <div class="p-2 bg-white rounded border-l-4 border-yellow-400">
          <div class="font-bold text-yellow-600">强制推送</div>
          <code class="text-xs">git push -f</code>
          <div class="text-xs mt-1 text-red-600">❌ 危险!会覆盖远程历史</div>
        </div>
      </div>
    </div>
  </div>

</div>

<div v-motion :initial="{ y: 30, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 1200 } }" class="mt-4">
  <div class="p-3 bg-gradient-to-r from-blue-50 to-cyan-50 rounded-lg border-2 border-blue-300 text-center">
    <div class="text-lg font-bold">💡 工作流程: <code class="bg-white px-2 py-1 rounded text-sm">pull</code> → 修改代码 → <code class="bg-white px-2 py-1 rounded text-sm">commit</code> → <code class="bg-white px-2 py-1 rounded text-sm">push</code></div>
  </div>
</div>

---
layout: center
---

<div class="text-center">
  <div class="text-6xl mb-6">🛠️</div>
  <h1 class="text-4xl font-bold text-yellow-600 mb-3">实用技巧与资源</h1>
  <p class="text-xl opacity-60">让你的 Git 使用更高效</p>
</div>

---
transition: slide-right
---

# 实战：完整的分支工作流

<div class="grid grid-cols-2 gap-6 mt-4">

  <div v-motion :initial="{ y: -50, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-5 bg-gradient-to-br from-blue-50 to-cyan-50 rounded-xl shadow-md">
      <h2 class="text-xl font-bold mb-4">阶段 1: 创建并开发</h2>
      <div class="bg-blue-50 border border-blue-300 text-gray-800 p-4 rounded-lg font-mono text-xs space-y-2">
        <div><span class="opacity-50"># 更新主分支</span></div>
        <div>git switch main && git pull</div>
        <div class="mt-2"><span class="opacity-50"># 创建功能分支</span></div>
        <div>git switch -c feat/error-handling</div>
        <div class="mt-2"><span class="opacity-50"># 开发并提交</span></div>
        <div>git add .</div>
        <div>git commit -m "feat: 添加错误处理"</div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ y: -50, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-5 bg-gradient-to-br from-green-50 to-emerald-100 rounded-xl shadow-md">
      <h2 class="text-xl font-bold mb-4">阶段 2: 合并回主分支</h2>
      <div class="bg-green-50 border border-green-300 text-gray-800 p-4 rounded-lg font-mono text-xs space-y-2">
        <div><span class="opacity-50"># 切回主分支并更新</span></div>
        <div>git switch main && git pull</div>
        <div class="mt-2"><span class="opacity-50"># 合并功能分支</span></div>
        <div>git merge feat/error-handling</div>
        <div class="mt-2"><span class="opacity-50"># 推送到远程</span></div>
        <div>git push origin main</div>
        <div class="mt-2"><span class="opacity-50"># 删除本地分支</span></div>
        <div>git branch -d feat/error-handling</div>
      </div>
    </div>
  </div>

</div>

---
transition: side-left
---

# Git 工作流：GitHub Flow

<div v-motion :initial="{ scale: 0.95, opacity: 0 }" :enter="{ scale: 1, opacity: 1, transition: { delay: 800 } }">
  <div class="p-5 bg-gradient-to-br from-blue-50 to-cyan-50 rounded-xl shadow-md mb-4">
    <h2 class="text-xl font-bold mb-3 flex items-center gap-2">
      <span class="text-3xl">🔄</span>
      <span>简单实用的团队协作模式</span>
    </h2>
    <div class="bg-blue-50 border border-blue-300 text-gray-800 p-4 rounded-lg font-mono text-sm">
      <div class="flex items-center gap-2">
        <span class="font-bold text-green-600">main</span>
        <span class="opacity-75">(生产环境)</span>
      </div>
      <div class="ml-4 mt-2">↓</div>
      <div class="ml-8 flex items-center gap-2 mt-1">
        <span class="font-bold text-blue-600">创建 feature 分支</span>
        <span>→</span>
        <span class="font-bold text-purple-600">开发</span>
        <span>→</span>
      </div>
      <div class="ml-8 flex items-center gap-2 mt-1">
        <span class="font-bold text-yellow-600">Pull Request</span>
        <span>→</span>
        <span class="font-bold text-orange-600">Code Review</span>
        <span>→</span>
        <span class="font-bold text-green-600">合并</span>
      </div>
    </div>
  </div>
</div>

<div class="grid grid-cols-3 gap-4 mt-4">
  <div v-motion :initial="{ y: 30, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-4 bg-green-50 rounded-xl shadow-sm">
      <div class="text-3xl mb-2">🔒</div>
      <div class="font-bold mb-2">原则 1</div>
      <div class="text-xs">main 永远可部署<br/><span class="opacity-75">(稳定版本)</span></div>
    </div>
  </div>

  <div v-motion :initial="{ y: 30, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-4 bg-blue-50 rounded-xl shadow-sm">
      <div class="text-3xl mb-2">🏷️</div>
      <div class="font-bold mb-2">原则 2</div>
      <div class="text-xs">描述性分支名<br/><code class="text-xs bg-white px-1 rounded">feature/user-auth</code></div>
    </div>
  </div>

  <div v-motion :initial="{ y: 30, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-4 bg-purple-50 rounded-xl shadow-sm">
      <div class="text-3xl mb-2">✅</div>
      <div class="font-bold mb-2">原则 3</div>
      <div class="text-xs">PR + Code Review<br/><span class="opacity-75">保证质量</span></div>
    </div>
  </div>

</div>


---
transition: slide-left
---

# 什么是 Pull Request (PR)?

<div v-motion :initial="{ scale: 0.95, opacity: 0 }" :enter="{ scale: 1, opacity: 1, transition: { delay: 800 } }">
  <div class="p-6 bg-gradient-to-br from-indigo-50 to-purple-100 rounded-xl shadow-md mb-6">
    <h2 class="text-2xl font-bold mb-3 flex items-center gap-2">
      <span class="text-4xl">🔄</span>
      <span>Pull Request 是什么?</span>
    </h2>
    <div class="bg-white p-4 rounded-lg text-base">
      <p class="mb-3">Pull Request (拉取请求) 是一种<span class="font-bold text-indigo-600">让别人审查你的代码</span>并<span class="font-bold text-indigo-600">合并到主分支</span>的机制。</p>
      <div class="bg-blue-50 border-l-4 border-blue-400 p-3 rounded">
        <div class="font-bold mb-1">通俗理解 📝</div>
        <div class="text-sm opacity-90">你在自己的分支上完成了功能开发，想要把代码合并到主分支。但不是直接合并，而是先"<span class="font-bold">请求</span>"项目维护者审查你的代码，觉得 OK 了再合并。</div>
      </div>
    </div>
  </div>
</div>

<div class="grid grid-cols-2 gap-4">
  <div v-motion :initial="{ x: -30, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 1000 } }">
    <div class="p-4 bg-green-50 rounded-xl">
      <div class="text-2xl mb-2">✅</div>
      <div class="font-bold mb-1">GitHub 叫 Pull Request</div>
      <div class="text-xs opacity-75">最常用的叫法</div>
    </div>
  </div>
  <div v-motion :initial="{ x: 30, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 1000 } }">
    <div class="p-4 bg-orange-50 rounded-xl">
      <div class="text-2xl mb-2">🦊</div>
      <div class="font-bold mb-1">GitLab 叫 Merge Request</div>
      <div class="text-xs opacity-75">意思一样，只是名字不同</div>
    </div>
  </div>
</div>

---
transition: fade
---

# 为什么要使用 Pull Request?

<div class="grid grid-cols-2 gap-5 mt-4">
  <div v-motion :initial="{ y: 30, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-5 bg-gradient-to-br from-blue-50 to-cyan-50 rounded-xl shadow-sm">
      <h2 class="text-xl font-bold mb-4 flex items-center gap-2">
        <span class="text-3xl">🛡️</span>
        <span>代码质量保障</span>
      </h2>
      <div class="space-y-3 text-sm">
        <div class="p-3 bg-white rounded-lg flex items-start gap-3">
          <span class="text-2xl">👀</span>
          <div>
            <div class="font-bold">代码审查 (Code Review)</div>
            <div class="text-xs opacity-75">多双眼睛看代码，找出 Bug 和问题</div>
          </div>
        </div>
        <div class="p-3 bg-white rounded-lg flex items-start gap-3">
          <span class="text-2xl">🤖</span>
          <div>
            <div class="font-bold">自动化测试</div>
            <div class="text-xs opacity-75">CI/CD 自动运行测试，确保代码可用</div>
          </div>
        </div>
        <div class="p-3 bg-white rounded-lg flex items-start gap-3">
          <span class="text-2xl">📏</span>
          <div>
            <div class="font-bold">代码规范检查</div>
            <div class="text-xs opacity-75">自动检查代码风格、格式是否统一</div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ y: 30, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-5 bg-gradient-to-br from-purple-50 to-pink-50 rounded-xl shadow-sm">
      <h2 class="text-xl font-bold mb-4 flex items-center gap-2">
        <span class="text-3xl">🤝</span>
        <span>团队协作</span>
      </h2>
      <div class="space-y-3 text-sm">
        <div class="p-3 bg-white rounded-lg flex items-start gap-3">
          <span class="text-2xl">💬</span>
          <div>
            <div class="font-bold">讨论和交流</div>
            <div class="text-xs opacity-75">在 PR 里讨论实现方案，分享想法</div>
          </div>
        </div>
        <div class="p-3 bg-white rounded-lg flex items-start gap-3">
          <span class="text-2xl">📚</span>
          <div>
            <div class="font-bold">知识传播</div>
            <div class="text-xs opacity-75">新人通过 Review 学习，老手传授经验</div>
          </div>
        </div>
        <div class="p-3 bg-white rounded-lg flex items-start gap-3">
          <span class="text-2xl">📝</span>
          <div>
            <div class="font-bold">留下记录</div>
            <div class="text-xs opacity-75">为什么这么改？讨论过程都有记录</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<div v-motion :initial="{ y: 30, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 1000 } }" class="mt-5 p-4 bg-green-50 rounded-xl border-l-4 border-green-400 flex items-start gap-3">
  <span class="text-3xl">💡</span>
  <div>
    <div class="font-bold">核心理念</div>
    <div class="text-sm opacity-75">PR 不是找茬，而是<span class="font-bold text-green-600">互相帮助</span>，共同提高代码质量！</div>
  </div>
</div>

---
transition: slide-up
---

# 如何使用 Pull Request?

<div v-motion :initial="{ scale: 0.95, opacity: 0 }" :enter="{ scale: 1, opacity: 1, transition: { delay: 800 } }">
  <div class="p-3 bg-gradient-to-br from-blue-50 to-indigo-50 rounded-xl shadow-sm mb-3">
    <h2 class="text-lg font-bold mb-2 flex items-center gap-2">
      <span class="text-2xl">🚀</span>
      <span>完整流程</span>
    </h2>
    <div class="flex items-center justify-center gap-1 text-xs">
      <div class="p-2 bg-white rounded text-center">
        <div class="text-lg mb-0.5">1️⃣</div>
        <div class="font-bold text-xs">创建分支</div>
      </div>
      <div class="text-lg">→</div>
      <div class="p-2 bg-white rounded text-center">
        <div class="text-lg mb-0.5">2️⃣</div>
        <div class="font-bold text-xs">开发提交</div>
      </div>
      <div class="text-lg">→</div>
      <div class="p-2 bg-white rounded text-center">
        <div class="text-lg mb-0.5">3️⃣</div>
        <div class="font-bold text-xs">推送远程</div>
      </div>
      <div class="text-lg">→</div>
      <div class="p-2 bg-purple-100 rounded text-center">
        <div class="text-lg mb-0.5">4️⃣</div>
        <div class="font-bold text-xs">创建 PR</div>
      </div>
      <div class="text-lg">→</div>
      <div class="p-2 bg-white rounded text-center">
        <div class="text-lg mb-0.5">5️⃣</div>
        <div class="font-bold text-xs">代码审查</div>
      </div>
      <div class="text-lg">→</div>
      <div class="p-2 bg-green-100 rounded text-center">
        <div class="text-lg mb-0.5">6️⃣</div>
        <div class="font-bold text-xs">合并代码</div>
      </div>
    </div>
  </div>
</div>

<div class="grid grid-cols-2 gap-3">
  <div v-motion :initial="{ x: -30, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 1000 } }">
    <div class="p-3 bg-yellow-50 rounded-xl">
      <h3 class="font-bold mb-2 flex items-center gap-2 text-sm">
        <span class="text-lg">📌</span>
        <span>创建 PR 的步骤</span>
      </h3>
      <div class="space-y-1 text-xs">
        <div class="bg-white p-1.5 rounded">1. 在 GitHub 点击 "New pull request"</div>
        <div class="bg-white p-1.5 rounded">2. 选择源分支 → 目标分支</div>
        <div class="bg-white p-1.5 rounded">3. 填写标题和描述</div>
        <div class="bg-white p-1.5 rounded">4. 指定审查者 (Reviewers)</div>
        <div class="bg-white p-1.5 rounded">5. 点击 "Create pull request"</div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ x: 30, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 1000 } }">
    <div class="p-3 bg-green-50 rounded-xl">
      <h3 class="font-bold mb-2 flex items-center gap-2 text-sm">
        <span class="text-lg">✅</span>
        <span>好的 PR 应该</span>
      </h3>
      <div class="space-y-1 text-xs">
        <div class="bg-white p-1.5 rounded flex items-center gap-1">
          <span>✓</span>
          <span><span class="font-bold">标题清晰</span>：feat: 添加登录功能</span>
        </div>
        <div class="bg-white p-1.5 rounded flex items-center gap-1">
          <span>✓</span>
          <span><span class="font-bold">描述完整</span>：改了什么、为什么</span>
        </div>
        <div class="bg-white p-1.5 rounded flex items-center gap-1">
          <span>✓</span>
          <span><span class="font-bold">一次一件事</span>：不混杂多个功能</span>
        </div>
        <div class="bg-white p-1.5 rounded flex items-center gap-1">
          <span>✓</span>
          <span><span class="font-bold">保持小巧</span>：改动不超过 300 行</span>
        </div>
        <div class="bg-white p-1.5 rounded flex items-center gap-1">
          <span>✓</span>
          <span><span class="font-bold">CI 通过</span>：确保测试都过了</span>
        </div>
      </div>
    </div>
  </div>
</div>

---
transition: fade
---

# Git 配置优化

<div class="grid grid-cols-2 gap-6 mt-6">

  <div v-motion :initial="{ x: -50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 200 } }">
    <div class="p-5 bg-gradient-to-br from-blue-50 to-blue-100 rounded-xl shadow-sm">
      <h2 class="text-xl font-bold mb-4 flex items-center gap-2">
        <span>命令别名</span>
      </h2>
      <p class="text-sm mb-3 opacity-75">让常用命令更简短</p>
      <div class="bg-blue-50 border-2 border-blue-200 p-3 rounded-lg text-sm font-mono space-y-1">
        <div>git config --global alias.st status</div>
        <div>git config --global alias.cm commit</div>
        <div>git config --global alias.lg "log --oneline"</div>
      </div>
      <div class="mt-3 text-xs opacity-75">
        之后就可以用 <code class="bg-white px-1 rounded">git st</code> 代替 <code class="bg-white px-1 rounded">git status</code>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ x: 50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 400 } }">
    <div class="p-5 bg-gradient-to-br from-green-50 to-emerald-100 rounded-xl shadow-sm">
      <h2 class="text-xl font-bold mb-4 flex items-center gap-2">
        <span>默认分支名</span>
      </h2>
      <p class="text-sm mb-3 opacity-75">新建仓库时使用 main 而不是 master</p>
      <div class="bg-green-50 border-2 border-green-200 p-3 rounded-lg text-sm font-mono">
        git config --global init.defaultBranch main
      </div>
      <div class="mt-3 p-2 bg-yellow-50 rounded text-xs flex items-center gap-2">
        <span>💡</span>
        <span>GitHub 等平台现在都默认使用 main</span>
      </div>
    </div>
  </div>

</div>

---
transition: slide-left
---

# 学习资源推荐

<div class="grid grid-cols-2 gap-6 mt-4">

  <div v-motion :initial="{ x: -50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 200 } }">
    <div class="p-5 bg-gradient-to-br from-purple-50 to-pink-50 rounded-xl shadow-sm">
      <h2 class="text-2xl mb-4 flex items-center gap-2">
        <span class="text-3xl">🎮</span>
        <span class="font-bold">互动学习</span>
      </h2>
      <div class="space-y-3 text-sm">
        <div class="p-3 bg-white rounded-lg shadow-sm border-l-4 border-purple-400">
          <div class="font-bold">Learn Git Branching</div>
          <div class="text-xs opacity-75 mt-1">可视化的交互式学习</div>
          <a href="https://learngitbranching.js.org" class="text-xs text-purple-600 underline">learngitbranching.js.org</a>
        </div>
        <div class="p-3 bg-white rounded-lg shadow-sm border-l-4 border-blue-400">
          <div class="font-bold">Pro Git 书籍</div>
          <div class="text-xs opacity-75 mt-1">免费在线阅读,最权威</div>
          <a href="https://git-scm.com/book/zh" class="text-xs text-blue-600 underline">git-scm.com/book/zh</a>
        </div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ x: 50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 400 } }">
    <div class="p-5 bg-gradient-to-br from-blue-50 to-cyan-50 rounded-xl shadow-sm">
      <h2 class="text-2xl mb-4 flex items-center gap-2">
        <span class="text-3xl">🛠️</span>
        <span class="font-bold">推荐工具</span>
      </h2>
      <div class="space-y-3 text-sm">
        <div class="p-3 bg-white rounded-lg shadow-sm flex items-start gap-3">
          <span class="text-2xl">💻</span>
          <div>
            <div class="font-bold">VSCode 内置 Git</div>
            <div class="text-xs opacity-75">侧边栏完成所有操作</div>
          </div>
        </div>
        <div class="p-3 bg-white rounded-lg shadow-sm flex items-start gap-3">
          <span class="text-2xl">🖱️</span>
          <div>
            <div class="font-bold">GitHub Desktop</div>
            <div class="text-xs opacity-75">图形界面,不用记命令</div>
          </div>
        </div>
        <div class="p-3 bg-white rounded-lg shadow-sm flex items-start gap-3">
          <span class="text-2xl">🌳</span>
          <div>
            <div class="font-bold">SourceTree</div>
            <div class="text-xs opacity-75">功能强大的图形工具</div>
          </div>
        </div>
      </div>
    </div>
  </div>

</div>

<div v-motion :initial="{ y: 20, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 600 } }" class="mt-6 p-4 bg-gradient-to-r from-green-50 to-emerald-50 rounded-xl border-2 border-green-200 text-center">

  <div class="text-lg font-bold">你总会找到一个让你舒适的 Git 使用方法</div>
  <div class="text-sm opacity-75 mt-1">命令行、图形界面、IDE 插件...选择最适合你的!</div>
</div>

---
transition: fade
---

# Git 是怎么工作的？

<div class="grid grid-cols-2 gap-4 mt-4">

  <div v-motion :initial="{ x: -50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 200 } }">
    <div class="p-4 bg-gradient-to-br from-blue-50 to-cyan-50 rounded-xl shadow-md">
      <h2 class="text-lg font-bold mb-3">Git 的三种核心对象</h2>
      <div class="space-y-2 text-sm">
        <div class="p-3 bg-white rounded-lg border-l-4 border-blue-400">
          <div class="font-bold mb-1">Blob</div>
          <div class="text-xs opacity-75">• 存储文件内容</div>
          <div class="text-xs opacity-75">• 用 SHA-1 标识</div>
        </div>
        <div class="p-3 bg-white rounded-lg border-l-4 border-green-400">
          <div class="font-bold mb-1">Tree</div>
          <div class="text-xs opacity-75">• 存储目录结构</div>
          <div class="text-xs opacity-75">• 包含 blob 和子 tree</div>
        </div>
        <div class="p-3 bg-white rounded-lg border-l-4 border-purple-400">
          <div class="font-bold mb-1">Commit</div>
          <div class="text-xs opacity-75">• 指向根 tree</div>
          <div class="text-xs opacity-75">• 包含作者、时间、消息</div>
        </div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ x: 50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 400 } }">
    <div class="p-4 bg-gradient-to-br from-purple-50 to-pink-50 rounded-xl shadow-md">
      <h2 class="text-lg font-bold mb-3">对象之间的关系</h2>
      <div class="bg-white p-3 rounded-lg text-sm font-mono border-2 border-purple-200">
        <div class="space-y-1">
          <div class="flex items-center gap-2">
            <span class="font-bold text-purple-600">Commit</span>
            <span>→</span>
            <span class="font-bold text-green-600">Tree</span>
          </div>
          <div class="ml-8 space-y-1">
            <div class="flex items-center gap-2">
              <span>├─</span>
              <span class="font-bold text-blue-600">Blob</span>
              <span class="text-xs opacity-60">(README.md)</span>
            </div>
            <div class="flex items-center gap-2">
              <span>├─</span>
              <span class="font-bold text-blue-600">Blob</span>
              <span class="text-xs opacity-60">(main.rs)</span>
            </div>
            <div class="flex items-center gap-2">
              <span>└─</span>
              <span class="font-bold text-green-600">Tree</span>
              <span class="text-xs opacity-60">(src/)</span>
            </div>
            <div class="ml-6 flex items-center gap-2">
              <span>└─</span>
              <span class="font-bold text-blue-600">Blob</span>
              <span class="text-xs opacity-60">(lib.rs)</span>
            </div>
          </div>
        </div>
      </div>
      <div class="mt-3 p-2 bg-yellow-50 rounded text-xs border-l-4 border-yellow-400">
        <strong>关键</strong>: 相同内容只存储一次,非常高效!
      </div>
    </div>
  </div>

</div>

---
layout: intro
transition: fade-out
---

# 总结

<div class="grid grid-cols-2 gap-6 mt-6">

  <div v-motion :initial="{ x: -50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-5 bg-gradient-to-br from-blue-50 to-cyan-50 rounded-xl border-2 border-blue-200">
      <h2 class="text-xl mb-4 flex items-center gap-2">
        <span>记住这些就够了</span>
      </h2>
      <div class="space-y-3 text-sm">
        <div class="flex items-start gap-3 p-2 bg-white rounded">
          <span class="font-bold text-blue-600">1</span>
          <div>
            <div class="font-bold">基本流程</div>
            <code class="text-xs bg-gray-100 px-2 py-1 rounded">git add → git commit → git push</code>
          </div>
        </div>
        <div class="flex items-start gap-3 p-2 bg-white rounded">
          <span class="font-bold text-blue-600">2</span>
          <div>
            <div class="font-bold">查看状态</div>
            <div class="text-xs opacity-75">随时 <code class="bg-gray-100 px-1 rounded">git status</code></div>
          </div>
        </div>
        <div class="flex items-start gap-3 p-2 bg-white rounded">
          <span class="font-bold text-blue-600">3</span>
          <div>
            <div class="font-bold">用好分支</div>
            <div class="text-xs opacity-75">开发新功能时创建新分支</div>
          </div>
        </div>
        <div class="flex items-start gap-3 p-2 bg-white rounded">
          <span class="font-bold text-blue-600">4</span>
          <div>
            <div class="font-bold">团队协作</div>
            <div class="text-xs opacity-75">先 pull,后 push</div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <div v-motion :initial="{ x: 50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800 } }">
    <div class="p-5 bg-gradient-to-br from-purple-50 to-pink-50 rounded-xl border-2 border-purple-200">
      <h2 class="text-xl mb-4 flex items-center gap-2">
        <span>Suggestions</span>
      </h2>
      <div class="space-y-3 text-sm">
        <div class="p-3 bg-white rounded-lg flex items-start gap-3">
          <div>
            <div class="font-bold">多练习</div>
            <div class="text-xs opacity-75">创建测试项目,试试所有命令</div>
          </div>
        </div>
        <div class="p-3 bg-white rounded-lg flex items-start gap-3">
          <div>
            <div class="font-bold">用 VSCode</div>
            <div class="text-xs opacity-75">图形界面更直观</div>
          </div>
        </div>
        <div class="p-3 bg-white rounded-lg flex items-start gap-3">
          <div>
            <div class="font-bold">看文档</div>
            <div class="text-xs opacity-75">遇到问题先搜索</div>
          </div>
        </div>
      </div>
    </div>
  </div></div>

---
layout: center
---

<div class="text-center">
  <h1 class="text-5xl font-bold text-green-600 mb-6">恭喜你迈出了第一步!</h1>
  
  <div class="text-2xl opacity-70 mb-12">
    Git 的学习是<span class="font-bold">持续的过程</span><br>
    今天学的这些，足够你完成<span class="font-bold">大部分日常工作</span>了
  </div>
  
  <div class="flex justify-center gap-16 text-lg">
    <div>
      <div class="text-4xl mb-2">📝</div>
      <div class="font-bold">掌握基础</div>
      <div class="text-sm opacity-60">add/commit/push</div>
    </div>
    <div>
      <div class="text-4xl mb-2">🌿</div>
      <div class="font-bold">理解分支</div>
      <div class="text-sm opacity-60">创建/合并/切换</div>
    </div>
    <div>
      <div class="text-4xl mb-2">👥</div>
      <div class="font-bold">团队协作</div>
      <div class="text-sm opacity-60">pull/push/冲突</div>
    </div>
  </div>
</div>

---
layout: center
---

<div class="text-center">
  <div class="text-5xl mb-6">🙋‍♂️</div>
  <h1 class="text-6xl font-bold text-blue-600 mb-4">Q & A</h1>
  <h2 class="text-3xl mb-10 opacity-70">有任何问题都可以提问!</h2>
  
  <div class="text-xl mb-8">
    💬 关于 Git 的<span class="font-bold">任何问题</span>都欢迎交流
  </div>
  
  <div class="flex justify-center gap-12 text-base">
    <div>
      <div class="text-3xl mb-2">📝</div>
      <div class="font-bold">基础命令</div>
    </div>
    <div>
      <div class="text-3xl mb-2">🌿</div>
      <div class="font-bold">分支管理</div>
    </div>
    <div>
      <div class="text-3xl mb-2">👥</div>
      <div class="font-bold">团队协作</div>
    </div>
  </div>
</div>

---
layout: center
---

<div class="text-center">
  <img src="/git-icon.png" class="inline-block w-24 h-24 mb-6" />
  
  <h1 class="text-6xl font-bold mb-4">Git 入门教程</h1>
  
  <p class="text-xl opacity-60 mb-10">
    一个为开发者设计的版本控制系统
  </p>
  
  <div class="text-lg opacity-50">
    软研部运维组
    <div class="mt-2">2025年10月19日</div>
  </div>
</div>
