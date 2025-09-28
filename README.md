<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ApprendsMoi'n - تطبيق التعلم التفاعلي</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700;900&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        primary: '#5D5CDE',
                        secondary: '#FF6B6B',
                        accent: '#4ECDC4',
                        success: '#45B7D1',
                        warning: '#F7B731',
                        danger: '#FF5252',
                        dark: '#2D3748'
                    },
                    fontFamily: {
                        'cairo': ['Cairo', 'sans-serif']
                    },
                    animation: {
                        'fade-in': 'fadeIn 0.6s ease-out',
                        'slide-up': 'slideUp 0.8s ease-out',
                        'slide-down': 'slideDown 0.6s ease-out',
                        'scale-in': 'scaleIn 0.5s ease-out',
                        'bounce-soft': 'bounceSoft 0.6s ease-out',
                        'float': 'float 3s ease-in-out infinite',
                        'pulse-soft': 'pulseSoft 2s ease-in-out infinite',
                        'gradient': 'gradient 8s ease infinite'
                    },
                    backgroundSize: {
                        '300%': '300%'
                    }
                }
            }
        }
    </script>
    <style>
        body { 
            font-family: 'Cairo', sans-serif; 
        }
        
        .gradient-bg { 
            background: linear-gradient(-45deg, #667eea, #764ba2, #f093fb, #f5576c, #4facfe, #00f2fe);
            background-size: 400% 400%;
            animation: gradient 15s ease infinite;
        }
        
        .glass-effect {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
        
        .dark .glass-effect {
            background: rgba(0, 0, 0, 0.2);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .card-hover {
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        .card-hover:hover {
            transform: translateY(-8px) scale(1.02);
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
        }
        
        .dark .card-hover:hover {
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.5);
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        @keyframes slideUp {
            from { opacity: 0; transform: translateY(50px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        @keyframes slideDown {
            from { opacity: 0; transform: translateY(-30px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        @keyframes scaleIn {
            from { opacity: 0; transform: scale(0.9); }
            to { opacity: 1; transform: scale(1); }
        }
        
        @keyframes bounceSoft {
            0%, 20%, 53%, 80%, 100% { transform: translate3d(0,0,0); }
            40%, 43% { transform: translate3d(0,-8px,0); }
            70% { transform: translate3d(0,-4px,0); }
            90% { transform: translate3d(0,-2px,0); }
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }
        
        @keyframes pulseSoft {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.7; }
        }
        
        @keyframes gradient {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }
        
        .tab-button {
            position: relative;
            overflow: hidden;
        }
        
        .tab-button::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transition: left 0.5s;
        }
        
        .tab-button:hover::before {
            left: 100%;
        }
        
        .floating-shapes {
            position: absolute;
            width: 100%;
            height: 100%;
            overflow: hidden;
            pointer-events: none;
        }
        
        .floating-shape {
            position: absolute;
            opacity: 0.1;
            animation: float 6s ease-in-out infinite;
        }
        
        .floating-shape:nth-child(1) { top: 20%; left: 10%; animation-delay: 0s; }
        .floating-shape:nth-child(2) { top: 60%; left: 80%; animation-delay: 2s; }
        .floating-shape:nth-child(3) { top: 40%; left: 60%; animation-delay: 4s; }
        
        .progress-indicator {
            height: 3px;
            background: linear-gradient(90deg, #5D5CDE, #4ECDC4);
            border-radius: 2px;
            transition: width 0.3s ease;
        }
        
        .typing-animation::after {
            content: '|';
            animation: blink 1s infinite;
        }
        
        @keyframes blink {
            0%, 50% { opacity: 1; }
            51%, 100% { opacity: 0; }
        }
        
        .custom-scrollbar::-webkit-scrollbar {
            width: 6px;
        }
        
        .custom-scrollbar::-webkit-scrollbar-track {
            background: #f1f1f1;
            border-radius: 3px;
        }
        
        .custom-scrollbar::-webkit-scrollbar-thumb {
            background: #888;
            border-radius: 3px;
        }
        
        .custom-scrollbar::-webkit-scrollbar-thumb:hover {
            background: #555;
        }
        
        .subject-icon {
            font-size: 2rem;
            margin-bottom: 1rem;
            transition: transform 0.3s ease;
        }
        
        .subject-card:hover .subject-icon {
            transform: scale(1.2) rotate(5deg);
        }
        
        .notification {
            transform: translateX(100%);
            transition: transform 0.3s ease;
        }
        
        .notification.show {
            transform: translateX(0);
        }
    </style>
</head>
<body class="bg-gray-50 dark:bg-gray-900 text-gray-900 dark:text-gray-100 overflow-x-hidden">
    <!-- Header -->
    <header class="fixed top-0 w-full z-50 glass-effect backdrop-blur-lg">
        <div class="container mx-auto px-4 py-4">
            <div class="flex items-center justify-between">
                <div class="flex items-center space-x-4 animate-slide-down">
                    <div class="text-3xl animate-bounce-soft">🎓</div>
                    <div>
                        <h1 class="text-2xl font-bold text-primary">ApprendsMoi'n</h1>
                        <p class="text-sm text-gray-600 dark:text-gray-400">تطبيق التعلم التفاعلي المتقدم</p>
                    </div>
                </div>
                <nav class="hidden md:flex space-x-8 animate-slide-down">
                    <a href="#" class="hover:text-primary transition-all duration-300 hover:scale-105">الرئيسية</a>
                    <a href="#" class="hover:text-primary transition-all duration-300 hover:scale-105">الدروس</a>
                    <a href="#" class="hover:text-primary transition-all duration-300 hover:scale-105">اختبار</a>
                    <a href="#" class="hover:text-primary transition-all duration-300 hover:scale-105">التقدم</a>
                    <a href="#" class="hover:text-primary transition-all duration-300 hover:scale-105">الملف</a>
                </nav>
                <button onclick="toggleMobileMenu()" class="md:hidden text-gray-600 dark:text-gray-400 hover:text-primary transition-colors">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
                    </svg>
                </button>
            </div>
        </div>
    </header>

    <!-- Mobile Menu -->
    <div id="mobile-menu" class="fixed top-0 right-0 w-64 h-full bg-white dark:bg-gray-800 shadow-2xl z-40 transform translate-x-full transition-transform duration-300">
        <div class="p-6 pt-20">
            <nav class="space-y-4">
                <a href="#" class="block hover:text-primary transition-colors">الرئيسية</a>
                <a href="#" class="block hover:text-primary transition-colors">الدروس</a>
                <a href="#" class="block hover:text-primary transition-colors">اختبار</a>
                <a href="#" class="block hover:text-primary transition-colors">التقدم</a>
                <a href="#" class="block hover:text-primary transition-colors">الملف</a>
            </nav>
        </div>
    </div>

    <!-- Loading Screen -->
    <div id="loading-screen" class="fixed inset-0 bg-gradient-to-br from-primary to-purple-600 flex items-center justify-center z-50">
        <div class="text-center">
            <div class="text-6xl mb-4 animate-bounce">🎓</div>
            <h2 class="text-2xl font-bold text-white mb-4">ApprendsMoi'n</h2>
            <div class="w-32 h-1 bg-white/30 rounded-full overflow-hidden">
                <div class="h-full bg-white rounded-full w-0 transition-all duration-2000" id="loading-bar"></div>
            </div>
        </div>
    </div>

    <!-- Level Selection Section -->
    <section id="level-selection" class="min-h-screen gradient-bg text-white relative pt-20">
        <div class="floating-shapes">
            <div class="floating-shape w-16 h-16 bg-white rounded-full"></div>
            <div class="floating-shape w-12 h-12 bg-white rounded-full"></div>
            <div class="floating-shape w-20 h-20 bg-white rounded-full"></div>
        </div>
        
        <div class="container mx-auto px-4 py-16 relative z-10">
            <div class="text-center mb-16">
                <h2 class="text-5xl md:text-6xl font-bold mb-6 animate-fade-in">مرحباً بك في ApprendsMoi'n</h2>
                <p class="text-xl md:text-2xl mb-8 animate-slide-up opacity-90">اختر مستواك التعليمي للبدء في رحلتك التعليمية التفاعلية</p>
                
                <!-- Enhanced Stats -->
                <div class="grid grid-cols-1 md:grid-cols-4 gap-8 mt-16 mb-16">
                    <div class="text-center animate-scale-in glass-effect rounded-xl p-6">
                        <div class="text-4xl font-bold mb-2 text-warning">500+</div>
                        <div class="text-lg">درس تفاعلي</div>
                    </div>
                    <div class="text-center animate-scale-in glass-effect rounded-xl p-6" style="animation-delay: 0.2s">
                        <div class="text-4xl font-bold mb-2 text-success">5,250</div>
                        <div class="text-lg">طالب نشط</div>
                    </div>
                    <div class="text-center animate-scale-in glass-effect rounded-xl p-6" style="animation-delay: 0.4s">
                        <div class="text-4xl font-bold mb-2 text-accent">98%</div>
                        <div class="text-lg">معدل النجاح</div>
                    </div>
                    <div class="text-center animate-scale-in glass-effect rounded-xl p-6" style="animation-delay: 0.6s">
                        <div class="text-4xl font-bold mb-2 text-secondary">24/7</div>
                        <div class="text-lg">دعم مستمر</div>
                    </div>
                </div>
            </div>

            <!-- Enhanced Level Cards -->
            <div class="grid grid-cols-1 lg:grid-cols-3 gap-8 max-w-7xl mx-auto">
                <div onclick="selectLevel('ابتدائي')" class="glass-effect rounded-3xl p-8 text-center cursor-pointer card-hover animate-slide-up">
                    <div class="text-7xl mb-6 animate-float">🎒</div>
                    <h3 class="text-3xl font-bold mb-4">المرحلة الابتدائية</h3>
                    <p class="text-lg mb-6 opacity-90">من الصف الأول إلى السادس الابتدائي</p>
                    <div class="text-sm opacity-80 mb-6 space-y-2">
                        <div class="flex items-center justify-center space-x-2">
                            <span>📚</span><span>أساسيات القراءة والكتابة</span>
                        </div>
                        <div class="flex items-center justify-center space-x-2">
                            <span>🧮</span><span>العمليات الحسابية البسيطة</span>
                        </div>
                        <div class="flex items-center justify-center space-x-2">
                            <span>🔬</span><span>العلوم الأساسية والاستكشاف</span>
                        </div>
                        <div class="flex items-center justify-center space-x-2">
                            <span>🎨</span><span>الأنشطة الفنية والإبداعية</span>
                        </div>
                    </div>
                    <button class="w-full bg-blue-500 hover:bg-blue-600 text-white py-4 px-6 rounded-xl font-bold transition-all duration-300 transform hover:scale-105 shadow-lg">
                        ابدأ رحلتك التعليمية الابتدائية
                    </button>
                    <div class="mt-4 text-sm opacity-70">
                        متوفر: 180+ درس تفاعلي
                    </div>
                </div>

                <div onclick="selectLevel('إعدادي')" class="glass-effect rounded-3xl p-8 text-center cursor-pointer card-hover animate-slide-up" style="animation-delay: 0.2s">
                    <div class="text-7xl mb-6 animate-float" style="animation-delay: 1s">📚</div>
                    <h3 class="text-3xl font-bold mb-4">المرحلة الإعدادية</h3>
                    <p class="text-lg mb-6 opacity-90">من الصف السابع إلى التاسع</p>
                    <div class="text-sm opacity-80 mb-6 space-y-2">
                        <div class="flex items-center justify-center space-x-2">
                            <span>🔢</span><span>الرياضيات المتقدمة والهندسة</span>
                        </div>
                        <div class="flex items-center justify-center space-x-2">
                            <span>⚗️</span><span>العلوم الطبيعية والتجارب</span>
                        </div>
                        <div class="flex items-center justify-center space-x-2">
                            <span>🌍</span><span>اللغات والثقافات العالمية</span>
                        </div>
                        <div class="flex items-center justify-center space-x-2">
                            <span>💻</span><span>تقنيات المعلومات الأساسية</span>
                        </div>
                    </div>
                    <button class="w-full bg-green-500 hover:bg-green-600 text-white py-4 px-6 rounded-xl font-bold transition-all duration-300 transform hover:scale-105 shadow-lg">
                        انطلق في المرحلة الإعدادية
                    </button>
                    <div class="mt-4 text-sm opacity-70">
                        متوفر: 240+ درس متخصص
                    </div>
                </div>

                <div onclick="selectLevel('ثانوي')" class="glass-effect rounded-3xl p-8 text-center cursor-pointer card-hover animate-slide-up" style="animation-delay: 0.4s">
                    <div class="text-7xl mb-6 animate-float" style="animation-delay: 2s">🎓</div>
                    <h3 class="text-3xl font-bold mb-4">المرحلة الثانوية</h3>
                    <p class="text-lg mb-6 opacity-90">من الصف العاشر إلى الثاني عشر</p>
                    <div class="text-sm opacity-80 mb-6 space-y-2">
                        <div class="flex items-center justify-center space-x-2">
                            <span>🧬</span><span>التخصصات العلمية المتقدمة</span>
                        </div>
                        <div class="flex items-center justify-center space-x-2">
                            <span>🏛️</span><span>الأدب والفلسفة والتاريخ</span>
                        </div>
                        <div class="flex items-center justify-center space-x-2">
                            <span>🎯</span><span>التحضير للجامعة والمستقبل</span>
                        </div>
                        <div class="flex items-center justify-center space-x-2">
                            <span>🚀</span><span>البحث العلمي والابتكار</span>
                        </div>
                    </div>
                    <button class="w-full bg-purple-500 hover:bg-purple-600 text-white py-4 px-6 rounded-xl font-bold transition-all duration-300 transform hover:scale-105 shadow-lg">
                        تفوق في المرحلة الثانوية
                    </button>
                    <div class="mt-4 text-sm opacity-70">
                        متوفر: 320+ درس احترافي
                    </div>
                </div>
            </div>

            <!-- Features Showcase -->
            <div class="mt-20 grid grid-cols-1 md:grid-cols-3 gap-8">
                <div class="text-center animate-fade-in" style="animation-delay: 0.8s">
                    <div class="text-4xl mb-4">🤖</div>
                    <h4 class="text-xl font-bold mb-2">ذكاء اصطناعي متقدم</h4>
                    <p class="opacity-80">مساعد تعليمي ذكي يجيب على أسئلتك فورياً</p>
                </div>
                <div class="text-center animate-fade-in" style="animation-delay: 1s">
                    <div class="text-4xl mb-4">📱</div>
                    <h4 class="text-xl font-bold mb-2">تعلم تفاعلي</h4>
                    <p class="opacity-80">فيديوهات ومحاكاة تفاعلية لفهم أعمق</p>
                </div>
                <div class="text-center animate-fade-in" style="animation-delay: 1.2s">
                    <div class="text-4xl mb-4">📊</div>
                    <h4 class="text-xl font-bold mb-2">تتبع التقدم</h4>
                    <p class="opacity-80">احصائيات مفصلة عن أدائك وتقدمك</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Main Content -->
    <main id="main-content" class="hidden min-h-screen bg-gray-50 dark:bg-gray-900 pt-20">
        <!-- Enhanced Level Header -->
        <div class="bg-white dark:bg-gray-800 shadow-xl rounded-2xl mx-4 mt-6 mb-8 overflow-hidden">
            <div class="relative">
                <div class="absolute inset-0 bg-gradient-to-r from-primary/10 to-purple-500/10"></div>
                <div class="relative p-8">
                    <div class="flex items-center justify-between">
                        <div class="flex items-center space-x-6">
                            <div class="text-5xl animate-bounce-soft" id="level-icon">🎓</div>
                            <div>
                                <h2 class="text-3xl font-bold" id="level-title">المرحلة الثانوية</h2>
                                <p class="text-gray-600 dark:text-gray-400 text-lg">تعلّم بسهولة مع دروس، فيديوهات، تمارين، واختبارات تفاعلية</p>
                                <div class="flex items-center space-x-4 mt-2">
                                    <span class="text-sm bg-primary/10 text-primary px-3 py-1 rounded-full" id="level-stats">320+ درس متاح</span>
                                    <span class="text-sm bg-green-100 text-green-600 px-3 py-1 rounded-full">متصل</span>
                                </div>
                            </div>
                        </div>
                        <div class="flex space-x-3">
                            <button onclick="showNotification('تم حفظ التقدم!')" class="px-4 py-2 bg-green-500 text-white rounded-lg hover:bg-green-600 transition-colors">
                                حفظ التقدم
                            </button>
                            <button onclick="goBackToLevelSelection()" class="px-4 py-2 bg-gray-500 text-white rounded-lg hover:bg-gray-600 transition-colors">
                                تغيير المستوى
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Enhanced Navigation Tabs -->
        <div class="container mx-auto px-4 mb-8">
            <div class="bg-white dark:bg-gray-800 rounded-2xl p-3 shadow-lg">
                <div class="flex flex-wrap justify-center space-x-2">
                    <button onclick="showSection('assistant')" id="tab-assistant" class="px-8 py-4 rounded-xl font-medium transition-all tab-button active flex items-center space-x-2">
                        <span>🤖</span><span>المساعد الذكي</span>
                    </button>
                    <button onclick="showSection('videos')" id="tab-videos" class="px-8 py-4 rounded-xl font-medium transition-all tab-button flex items-center space-x-2">
                        <span>📹</span><span>الدروس المرئية</span>
                    </button>
                    <button onclick="showSection('written')" id="tab-written" class="px-8 py-4 rounded-xl font-medium transition-all tab-button flex items-center space-x-2">
                        <span>📚</span><span>الدروس المكتوبة</span>
                    </button>
                    <button onclick="showSection('exams')" id="tab-exams" class="px-8 py-4 rounded-xl font-medium transition-all tab-button flex items-center space-x-2">
                        <span>📝</span><span>الفروض والامتحانات</span>
                    </button>
                </div>
            </div>
        </div>

        <div class="container mx-auto px-4 pb-12">
            <!-- Enhanced AI Assistant Section -->
            <section id="section-assistant" class="section-content">
                <div class="bg-white dark:bg-gray-800 rounded-2xl shadow-xl p-8 mb-8">
                    <div class="text-center mb-8">
                        <h3 class="text-3xl font-bold mb-4 text-primary">المساعد التعليمي الذكي المتقدم</h3>
                        <p class="text-xl text-gray-600 dark:text-gray-400">اسأل أي سؤال واحصل على إجابة فورية ومفصلة مع أمثلة تطبيقية</p>
                    </div>
                    
                    <div class="grid grid-cols-1 lg:grid-cols-3 gap-6 mb-8">
                        <div>
                            <label class="block text-sm font-medium mb-3">اختر المادة:</label>
                            <select class="w-full p-4 border-2 border-gray-300 dark:border-gray-600 rounded-xl dark:bg-gray-700 text-base focus:border-primary transition-colors">
                                <option>جميع المواد</option>
                                <option>رياضيات</option>
                                <option>فيزياء</option>
                                <option>كيمياء</option>
                                <option>علوم الحياة والأرض</option>
                                <option>لغة عربية</option>
                                <option>لغة إنجليزية</option>
                                <option>لغة فرنسية</option>
                                <option>اجتماعيات</option>
                            </select>
                        </div>
                        <div>
                            <label class="block text-sm font-medium mb-3">مستوى الصعوبة:</label>
                            <select class="w-full p-4 border-2 border-gray-300 dark:border-gray-600 rounded-xl dark:bg-gray-700 text-base focus:border-primary transition-colors">
                                <option>أساسي</option>
                                <option>متوسط</option>
                                <option>متقدم</option>
                                <option>خبير</option>
                            </select>
                        </div>
                        <div>
                            <label class="block text-sm font-medium mb-3">نوع الإجابة:</label>
                            <select class="w-full p-4 border-2 border-gray-300 dark:border-gray-600 rounded-xl dark:bg-gray-700 text-base focus:border-primary transition-colors">
                                <option>شرح مفصل</option>
                                <option>خطوات الحل</option>
                                <option>أمثلة تطبيقية</option>
                                <option>ملخص سريع</option>
                            </select>
                        </div>
                    </div>

                    <div class="bg-gradient-to-r from-blue-50 to-purple-50 dark:from-blue-900/20 dark:to-purple-900/20 rounded-2xl p-8 mb-8">
                        <div class="flex items-start space-x-4">
                            <div class="text-3xl animate-pulse-soft">🤖</div>
                            <div class="flex-1">
                                <h4 class="font-bold text-lg mb-2">مرحباً! أنا مساعدك التعليمي الذكي المتطور</h4>
                                <p class="text-gray-700 dark:text-gray-300 mb-4">يمكنني مساعدتك في أي مادة دراسية بطرق متنوعة:</p>
                                <ul class="text-sm space-y-1 text-gray-600 dark:text-gray-400">
                                    <li>• شرح المفاهيم الصعبة بطريقة مبسطة</li>
                                    <li>• حل المسائل خطوة بخطوة</li>
                                    <li>• تقديم أمثلة من الحياة الواقعية</li>
                                    <li>• إنشاء خطط دراسية مخصصة</li>
                                </ul>
                            </div>
                        </div>
                    </div>

                    <div class="mb-8">
                        <h5 class="text-lg font-medium mb-4">أسئلة سريعة شائعة:</h5>
                        <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                            <button onclick="askQuestion('قانون نيوتن الأول')" class="p-4 bg-blue-100 dark:bg-blue-900 text-blue-800 dark:text-blue-200 rounded-xl text-sm hover:bg-blue-200 dark:hover:bg-blue-800 transition-all transform hover:scale-105 text-right">
                                <div class="font-bold mb-1">⚛️ قانون نيوتن الأول</div>
                                <div class="text-xs opacity-75">الفيزياء - قوانين الحركة</div>
                            </button>
                            <button onclick="askQuestion('المعادلات التربيعية')" class="p-4 bg-green-100 dark:bg-green-900 text-green-800 dark:text-green-200 rounded-xl text-sm hover:bg-green-200 dark:hover:bg-green-800 transition-all transform hover:scale-105 text-right">
                                <div class="font-bold mb-1">📊 المعادلات التربيعية</div>
                                <div class="text-xs opacity-75">الرياضيات - الجبر</div>
                            </button>
                            <button onclick="askQuestion('أجزاء الخلية')" class="p-4 bg-purple-100 dark:bg-purple-900 text-purple-800 dark:text-purple-200 rounded-xl text-sm hover:bg-purple-200 dark:hover:bg-purple-800 transition-all transform hover:scale-105 text-right">
                                <div class="font-bold mb-1">🔬 أجزاء الخلية</div>
                                <div class="text-xs opacity-75">علوم الحياة والأرض</div>
                            </button>
                        </div>
                    </div>

                    <div class="relative">
                        <input type="text" id="question-input" placeholder="اكتب سؤالك هنا... (مثال: اشرح لي قانون الجاذبية بطريقة مبسطة)" class="w-full p-4 pr-16 border-2 border-gray-300 dark:border-gray-600 rounded-xl dark:bg-gray-700 text-base focus:border-primary transition-colors">
                        <button onclick="sendQuestion()" class="absolute left-2 top-2 bottom-2 px-6 bg-primary text-white rounded-lg hover:bg-primary/90 transition-colors flex items-center space-x-2">
                            <span>إرسال</span>
                            <span>🚀</span>
                        </button>
                    </div>

                    <div id="ai-response" class="mt-8 hidden">
                        <div class="bg-gradient-to-r from-blue-50 to-green-50 dark:from-blue-900/20 dark:to-green-900/20 border-2 border-blue-200 dark:border-blue-800 rounded-2xl p-6">
                            <div class="flex items-center space-x-3 mb-4">
                                <div class="text-2xl">🎯</div>
                                <h4 class="text-lg font-bold">إجابة المساعد الذكي</h4>
                            </div>
                            <div id="response-content" class="prose dark:prose-invert max-w-none"></div>
                            <div class="mt-4 flex items-center space-x-4 text-sm text-gray-600 dark:text-gray-400">
                                <button onclick="likeResponse()" class="flex items-center space-x-1 hover:text-green-600 transition-colors">
                                    <span>👍</span><span>مفيد</span>
                                </button>
                                <button onclick="shareResponse()" class="flex items-center space-x-1 hover:text-blue-600 transition-colors">
                                    <span>📤</span><span>مشاركة</span>
                                </button>
                                <button onclick="saveResponse()" class="flex items-center space-x-1 hover:text-purple-600 transition-colors">
                                    <span>🔖</span><span>حفظ</span>
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

            <!-- Enhanced Video Lessons Section -->
            <section id="section-videos" class="section-content hidden">
                <div class="bg-white dark:bg-gray-800 rounded-2xl shadow-xl p-8">
                    <div class="flex justify-between items-center mb-8">
                        <div>
                            <h3 class="text-3xl font-bold mb-2">مكتبة الدروس المرئية التفاعلية</h3>
                            <p class="text-gray-600 dark:text-gray-400">اكتشف مجموعة واسعة من الدروس المرئية عالية الجودة</p>
                        </div>
                        <button class="px-6 py-3 bg-primary text-white rounded-xl hover:bg-primary/90 transition-colors flex items-center space-x-2">
                            <span>➕</span><span>إنشاء درس جديد</span>
                        </button>
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-4 gap-6 mb-8">
                        <select class="p-4 border-2 border-gray-300 dark:border-gray-600 rounded-xl dark:bg-gray-700 text-base focus:border-primary transition-colors">
                            <option>جميع المواد</option>
                            <option>رياضيات</option>
                            <option>فيزياء</option>
                            <option>كيمياء</option>
                            <option>علوم الحياة والأرض</option>
                            <option>لغة عربية</option>
                            <option>لغة إنجليزية</option>
                            <option>لغة فرنسية</option>
                            <option>اجتماعيات</option>
                        </select>
                        <select class="p-4 border-2 border-gray-300 dark:border-gray-600 rounded-xl dark:bg-gray-700 text-base focus:border-primary transition-colors">
                            <option>جميع المستويات</option>
                            <option>ابتدائي</option>
                            <option>إعدادي</option>
                            <option>ثانوي</option>
                        </select>
                        <select class="p-4 border-2 border-gray-300 dark:border-gray-600 rounded-xl dark:bg-gray-700 text-base focus:border-primary transition-colors">
                            <option>الأحدث</option>
                            <option>الأكثر مشاهدة</option>
                            <option>الأعلى تقييماً</option>
                            <option>الأقصر مدة</option>
                        </select>
                        <input type="search" placeholder="البحث في الدروس..." class="p-4 border-2 border-gray-300 dark:border-gray-600 rounded-xl dark:bg-gray-700 text-base focus:border-primary transition-colors">
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
                        <div class="bg-gray-50 dark:bg-gray-700 rounded-2xl p-6 card-hover">
                            <div class="relative mb-4">
                                <div class="w-full h-48 bg-gradient-to-br from-blue-400 to-purple-600 rounded-xl flex items-center justify-center">
                                    <div class="text-6xl opacity-80">▶️</div>
                                </div>
                                <div class="absolute top-4 right-4 bg-black/50 text-white px-2 py-1 rounded text-sm">25:30</div>
                                <div class="absolute bottom-4 right-4 bg-red-500 text-white px-2 py-1 rounded text-xs">جديد</div>
                            </div>
                            <h4 class="font-bold text-xl mb-2">المعادلات التربيعية - شرح شامل</h4>
                            <p class="text-gray-600 dark:text-gray-400 mb-4 text-sm">شرح مفصل للمعادلات التربيعية مع حل الأمثلة خطوة بخطوة</p>
                            <div class="flex items-center justify-between text-sm text-gray-500 dark:text-gray-400 mb-4">
                                <span class="flex items-center space-x-1"><span>📚</span><span>رياضيات</span></span>
                                <span class="flex items-center space-x-1"><span>🎓</span><span>ثانوي</span></span>
                                <span class="flex items-center space-x-1"><span>👀</span><span>1,234</span></span>
                                <span class="flex items-center space-x-1"><span>⭐</span><span>4.8</span></span>
                            </div>
                            <div class="flex space-x-2">
                                <button class="flex-1 px-4 py-3 bg-blue-500 text-white rounded-xl hover:bg-blue-600 transition-colors">مشاهدة الآن</button>
                                <button class="px-4 py-3 border border-gray-300 dark:border-gray-600 rounded-xl hover:bg-gray-100 dark:hover:bg-gray-600 transition-colors">🔖</button>
                            </div>
                        </div>

                        <div class="bg-gray-50 dark:bg-gray-700 rounded-2xl p-6 card-hover">
                            <div class="relative mb-4">
                                <div class="w-full h-48 bg-gradient-to-br from-green-400 to-blue-600 rounded-xl flex items-center justify-center">
                                    <div class="text-6xl opacity-80">▶️</div>
                                </div>
                                <div class="absolute top-4 right-4 bg-black/50 text-white px-2 py-1 rounded text-sm">18:45</div>
                                <div class="absolute bottom-4 right-4 bg-yellow-500 text-white px-2 py-1 rounded text-xs">شائع</div>
                            </div>
                            <h4 class="font-bold text-xl mb-2">قوانين نيوتن للحركة</h4>
                            <p class="text-gray-600 dark:text-gray-400 mb-4 text-sm">دراسة القوانين الثلاثة لنيوتن مع تجارب تفاعلية</p>
                            <div class="flex items-center justify-between text-sm text-gray-500 dark:text-gray-400 mb-4">
                                <span class="flex items-center space-x-1"><span>⚡</span><span>فيزياء</span></span>
                                <span class="flex items-center space-x-1"><span>🎓</span><span>ثانوي</span></span>
                                <span class="flex items-center space-x-1"><span>👀</span><span>2,567</span></span>
                                <span class="flex items-center space-x-1"><span>⭐</span><span>4.9</span></span>
                            </div>
                            <div class="flex space-x-2">
                                <button class="flex-1 px-4 py-3 bg-blue-500 text-white rounded-xl hover:bg-blue-600 transition-colors">مشاهدة الآن</button>
                                <button class="px-4 py-3 border border-gray-300 dark:border-gray-600 rounded-xl hover:bg-gray-100 dark:hover:bg-gray-600 transition-colors">🔖</button>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

            <!-- Enhanced Written Lessons Section -->
            <section id="section-written" class="section-content hidden">
                <div class="bg-white dark:bg-gray-800 rounded-2xl shadow-xl p-8">
                    <div class="flex justify-between items-center mb-8">
                        <div>
                            <h3 class="text-3xl font-bold mb-2">مكتبة الدروس المكتوبة الشاملة</h3>
                            <p class="text-gray-600 dark:text-gray-400">ملخصات مفصلة وشروحات تفاعلية لجميع المواد</p>
                        </div>
                        <button class="px-6 py-3 bg-primary text-white rounded-xl hover:bg-primary/90 transition-colors flex items-center space-x-2">
                            <span>📝</span><span>إنشاء ملخص جديد</span>
                        </button>
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-4 gap-6 mb-8">
                        <select class="p-4 border-2 border-gray-300 dark:border-gray-600 rounded-xl dark:bg-gray-700 text-base focus:border-primary transition-colors">
                            <option>جميع المواد</option>
                            <option>رياضيات</option>
                            <option>فيزياء</option>
                            <option>كيمياء</option>
                            <option>علوم الحياة والأرض</option>
                            <option>لغة عربية</option>
                            <option>لغة إنجليزية</option>
                            <option>لغة فرنسية</option>
                            <option>اجتماعيات</option>
                        </select>
                        <select class="p-4 border-2 border-gray-300 dark:border-gray-600 rounded-xl dark:bg-gray-700 text-base focus:border-primary transition-colors">
                            <option>جميع المستويات</option>
                            <option>ابتدائي</option>
                            <option>إعدادي</option>
                            <option>ثانوي</option>
                        </select>
                        <select class="p-4 border-2 border-gray-300 dark:border-gray-600 rounded-xl dark:bg-gray-700 text-base focus:border-primary transition-colors">
                            <option>الأحدث</option>
                            <option>الأكثر قراءة</option>
                            <option>الأعلى تقييماً</option>
                            <option>الأقصر مدة</option>
                        </select>
                        <input type="search" placeholder="البحث في الملخصات..." class="p-4 border-2 border-gray-300 dark:border-gray-600 rounded-xl dark:bg-gray-700 text-base focus:border-primary transition-colors">
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-3 gap-6">
                        <div class="bg-gradient-to-br from-blue-50 to-indigo-100 dark:from-blue-900/20 dark:to-indigo-900/20 rounded-2xl p-6 card-hover border border-blue-200 dark:border-blue-800">
                            <div class="flex items-center justify-between mb-4">
                                <div class="text-3xl">📊</div>
                                <span class="text-xs bg-blue-500 text-white px-2 py-1 rounded-full">جديد</span>
                            </div>
                            <h4 class="font-bold text-xl mb-3">المعادلات التربيعية</h4>
                            <p class="text-gray-600 dark:text-gray-400 mb-4 text-sm leading-relaxed">شرح شامل لحل المعادلات التربيعية بالطرق المختلفة مع أمثلة تطبيقية ورسوم بيانية توضيحية</p>
                            <div class="flex items-center justify-between text-sm text-gray-500 dark:text-gray-400 mb-4">
                                <span class="flex items-center space-x-1"><span>📚</span><span>رياضيات</span></span>
                                <span class="flex items-center space-x-1"><span>🎓</span><span>ثانوي</span></span>
                                <span class="flex items-center space-x-1"><span>⏱️</span><span>15 دقيقة</span></span>
                            </div>
                            <div class="flex items-center justify-between text-xs text-gray-500 dark:text-gray-400 mb-4">
                                <span>👁️ 1,234 قراءة</span>
                                <span>⭐ 4.8 تقييم</span>
                                <span>💬 25 تعليق</span>
                            </div>
                            <button class="w-full px-4 py-3 bg-blue-500 text-white rounded-xl hover:bg-blue-600 transition-colors font-medium">قراءة الملخص</button>
                        </div>

                        <div class="bg-gradient-to-br from-green-50 to-emerald-100 dark:from-green-900/20 dark:to-emerald-900/20 rounded-2xl p-6 card-hover border border-green-200 dark:border-green-800">
                            <div class="flex items-center justify-between mb-4">
                                <div class="text-3xl">⚡</div>
                                <span class="text-xs bg-green-500 text-white px-2 py-1 rounded-full">شائع</span>
                            </div>
                            <h4 class="font-bold text-xl mb-3">قوانين نيوتن للحركة</h4>
                            <p class="text-gray-600 dark:text-gray-400 mb-4 text-sm leading-relaxed">دراسة القوانين الثلاثة لنيوتن وتطبيقاتها في الحياة اليومية مع تجارب عملية</p>
                            <div class="flex items-center justify-between text-sm text-gray-500 dark:text-gray-400 mb-4">
                                <span class="flex items-center space-x-1"><span>⚡</span><span>فيزياء</span></span>
                                <span class="flex items-center space-x-1"><span>🎓</span><span>ثانوي</span></span>
                                <span class="flex items-center space-x-1"><span>⏱️</span><span>20 دقيقة</span></span>
                            </div>
                            <div class="flex items-center justify-between text-xs text-gray-500 dark:text-gray-400 mb-4">
                                <span>👁️ 2,567 قراءة</span>
                                <span>⭐ 4.9 تقييم</span>
                                <span>💬 42 تعليق</span>
                            </div>
                            <button class="w-full px-4 py-3 bg-green-500 text-white rounded-xl hover:bg-green-600 transition-colors font-medium">قراءة الملخص</button>
                        </div>

                        <div class="bg-gradient-to-br from-purple-50 to-violet-100 dark:from-purple-900/20 dark:to-violet-900/20 rounded-2xl p-6 card-hover border border-purple-200 dark:border-purple-800">
                            <div class="flex items-center justify-between mb-4">
                                <div class="text-3xl">📖</div>
                                <span class="text-xs bg-purple-500 text-white px-2 py-1 rounded-full">مميز</span>
                            </div>
                            <h4 class="font-bold text-xl mb-3">النحو العربي - الإعراب</h4>
                            <p class="text-gray-600 dark:text-gray-400 mb-4 text-sm leading-relaxed">قواعد الإعراب في اللغة العربية مع أمثلة تطبيقية متنوعة وخرائط ذهنية</p>
                            <div class="flex items-center justify-between text-sm text-gray-500 dark:text-gray-400 mb-4">
                                <span class="flex items-center space-x-1"><span>📖</span><span>لغة عربية</span></span>
                                <span class="flex items-center space-x-1"><span>🎓</span><span>إعدادي</span></span>
                                <span class="flex items-center space-x-1"><span>⏱️</span><span>22 دقيقة</span></span>
                            </div>
                            <div class="flex items-center justify-between text-xs text-gray-500 dark:text-gray-400 mb-4">
                                <span>👁️ 1,876 قراءة</span>
                                <span>⭐ 4.7 تقييم</span>
                                <span>💬 18 تعليق</span>
                            </div>
                            <button class="w-full px-4 py-3 bg-purple-500 text-white rounded-xl hover:bg-purple-600 transition-colors font-medium">قراءة الملخص</button>
                        </div>
                    </div>
                </div>
            </section>

            <!-- Enhanced Exams Section -->
            <section id="section-exams" class="section-content hidden">
                <div class="bg-white dark:bg-gray-800 rounded-2xl shadow-xl p-8">
                    <div class="flex justify-between items-center mb-8">
                        <div>
                            <h3 class="text-3xl font-bold mb-2">مركز الفروض والامتحانات المتقدم</h3>
                            <p class="text-gray-600 dark:text-gray-400">أنشئ وحل امتحانات ذكية مخصصة لمستواك</p>
                        </div>
                        <button class="px-6 py-3 bg-primary text-white rounded-xl hover:bg-primary/90 transition-colors flex items-center space-x-2">
                            <span>🎯</span><span>إنشاء امتحان ذكي</span>
                        </button>
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                        <div class="bg-gradient-to-br from-blue-50 to-purple-50 dark:from-blue-900/20 dark:to-purple-900/20 rounded-2xl p-8 border border-blue-200 dark:border-blue-800">
                            <h4 class="text-2xl font-bold mb-6 flex items-center space-x-2">
                                <span>🤖</span><span>إنشاء امتحان بالذكاء الاصطناعي</span>
                            </h4>
                            
                            <div class="space-y-6">
                                <div>
                                    <label class="block text-sm font-medium mb-3">اختر المادة</label>
                                    <select class="w-full p-4 border-2 border-gray-300 dark:border-gray-600 rounded-xl dark:bg-gray-600 text-base focus:border-primary transition-colors">
                                        <option>رياضيات</option>
                                        <option>فيزياء</option>
                                        <option>كيمياء</option>
                                        <option>علوم الحياة والأرض</option>
                                        <option>لغة عربية</option>
                                        <option>لغة إنجليزية</option>
                                        <option>لغة فرنسية</option>
                                        <option>اجتماعيات</option>
                                    </select>
                                </div>

                                <div class="grid grid-cols-2 gap-4">
                                    <div>
                                        <label class="block text-sm font-medium mb-3">المستوى</label>
                                        <select class="w-full p-4 border-2 border-gray-300 dark:border-gray-600 rounded-xl dark:bg-gray-600 text-base focus:border-primary transition-colors">
                                            <option>ابتدائي</option>
                                            <option>إعدادي</option>
                                            <option>ثانوي</option>
                                        </select>
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium mb-3">الصعوبة</label>
                                        <select class="w-full p-4 border-2 border-gray-300 dark:border-gray-600 rounded-xl dark:bg-gray-600 text-base focus:border-primary transition-colors">
                                            <option>سهل</option>
                                            <option>متوسط</option>
                                            <option>صعب</option>
                                        </select>
                                    </div>
                                </div>

                                <div class="grid grid-cols-2 gap-4">
                                    <div>
                                        <label class="block text-sm font-medium mb-3">نوع الامتحان</label>
                                        <select class="w-full p-4 border-2 border-gray-300 dark:border-gray-600 rounded-xl dark:bg-gray-600 text-base focus:border-primary transition-colors">
                                            <option>فرض محروس</option>
                                            <option>امتحان فصلي</option>
                                            <option>تمارين تطبيقية</option>
                                            <option>مراجعة شاملة</option>
                                        </select>
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium mb-3">مدة الامتحان</label>
                                        <select class="w-full p-4 border-2 border-gray-300 dark:border-gray-600 rounded-xl dark:bg-gray-600 text-base focus:border-primary transition-colors">
                                            <option>30 دقيقة</option>
                                            <option>ساعة واحدة</option>
                                            <option>ساعة ونصف</option>
                                            <option>ساعتان</option>
                                        </select>
                                    </div>
                                </div>

                                <div>
                                    <label class="block text-sm font-medium mb-3">عدد الأسئلة</label>
                                    <input type="range" min="5" max="30" value="15" class="w-full mb-2" id="question-count">
                                    <div class="text-center text-sm text-gray-600 dark:text-gray-400">
                                        <span id="question-count-display">15</span> سؤال
                                    </div>
                                </div>

                                <button onclick="generateExam()" class="w-full px-6 py-4 bg-gradient-to-r from-primary to-purple-600 text-white rounded-xl hover:from-primary/90 hover:to-purple-600/90 transition-all font-bold text-lg transform hover:scale-105 shadow-lg">
                                    🚀 إنشاء الامتحان الآن
                                </button>
                            </div>
                        </div>

                        <div class="bg-gradient-to-br from-green-50 to-blue-50 dark:from-green-900/20 dark:to-blue-900/20 rounded-2xl p-8 border border-green-200 dark:border-green-800">
                            <div class="flex justify-between items-center mb-6">
                                <h4 class="text-2xl font-bold flex items-center space-x-2">
                                    <span>📚</span><span>مكتبة الامتحانات المتقدمة</span>
                                </h4>
                                <div class="flex space-x-2">
                                    <button onclick="showImportModal()" class="px-3 py-2 bg-purple-500 text-white rounded-lg text-sm hover:bg-purple-600 transition-colors flex items-center space-x-1">
                                        <span>📥</span><span>استيراد</span>
                                    </button>
                                    <button onclick="toggleExamView()" class="px-3 py-2 bg-gray-500 text-white rounded-lg text-sm hover:bg-gray-600 transition-colors">
                                        <span id="view-toggle-text">🔍 عرض الكل</span>
                                    </button>
                                </div>
                            </div>

                            <!-- Filter and Search -->
                            <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-6">
                                <select id="exam-subject-filter" onchange="filterExams()" class="p-3 border border-gray-300 dark:border-gray-600 rounded-lg dark:bg-gray-600 text-sm focus:border-primary transition-colors">
                                    <option value="all">جميع المواد</option>
                                    <option value="رياضيات">رياضيات</option>
                                    <option value="فيزياء">فيزياء</option>
                                    <option value="كيمياء">كيمياء</option>
                                    <option value="علوم الحياة والأرض">علوم الحياة والأرض</option>
                                    <option value="لغة عربية">لغة عربية</option>
                                    <option value="لغة إنجليزية">لغة إنجليزية</option>
                                    <option value="اجتماعيات">اجتماعيات</option>
                                </select>
                                <select id="exam-level-filter" onchange="filterExams()" class="p-3 border border-gray-300 dark:border-gray-600 rounded-lg dark:bg-gray-600 text-sm focus:border-primary transition-colors">
                                    <option value="all">جميع المستويات</option>
                                    <option value="ابتدائي">ابتدائي</option>
                                    <option value="إعدادي">إعدادي</option>
                                    <option value="ثانوي">ثانوي</option>
                                </select>
                                <input type="search" id="exam-search" oninput="filterExams()" placeholder="البحث في الامتحانات..." class="p-3 border border-gray-300 dark:border-gray-600 rounded-lg dark:bg-gray-600 text-sm focus:border-primary transition-colors">
                            </div>
                            
                            <div id="exams-container" class="space-y-4 max-h-96 overflow-y-auto custom-scrollbar">
                                <!-- Exams will be loaded here dynamically -->
                            </div>

                            <div class="mt-6 text-center">
                                <button onclick="loadMoreExams()" id="load-more-btn" class="px-6 py-2 bg-blue-500 text-white rounded-lg text-sm hover:bg-blue-600 transition-colors">
                                    تحميل المزيد من الامتحانات
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            </section>
        </div>
    </main>

    <!-- Notification Toast -->
    <div id="notification" class="fixed top-24 left-4 bg-white dark:bg-gray-800 shadow-xl rounded-xl p-4 notification z-50 border border-gray-200 dark:border-gray-700">
        <div class="flex items-center space-x-3">
            <div class="text-2xl">✅</div>
            <div>
                <div class="font-bold text-sm" id="notification-title">نجح!</div>
                <div class="text-xs text-gray-600 dark:text-gray-400" id="notification-message">تم بنجاح</div>
            </div>
        </div>
    </div>

    <script>
        // Dark mode detection
        if (window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches) {
            document.documentElement.classList.add('dark');
        }
        window.matchMedia('(prefers-color-scheme: dark)').addEventListener('change', event => {
            if (event.matches) {
                document.documentElement.classList.add('dark');
            } else {
                document.documentElement.classList.remove('dark');
            }
        });

        // Loading screen
        window.addEventListener('load', function() {
            const loadingBar = document.getElementById('loading-bar');
            let width = 0;
            const interval = setInterval(() => {
                width += Math.random() * 15;
                if (width >= 100) {
                    width = 100;
                    clearInterval(interval);
                    setTimeout(() => {
                        document.getElementById('loading-screen').classList.add('hidden');
                    }, 500);
                }
                loadingBar.style.width = width + '%';
            }, 100);
        });

        // Mobile menu toggle
        function toggleMobileMenu() {
            const menu = document.getElementById('mobile-menu');
            menu.classList.toggle('translate-x-full');
        }

        // Question count slider
        document.getElementById('question-count').addEventListener('input', function() {
            document.getElementById('question-count-display').textContent = this.value;
        });

        // Level selection functionality
        let selectedLevel = '';
        
        function selectLevel(level) {
            selectedLevel = level;
            
            // Hide level selection screen with animation
            const levelSection = document.getElementById('level-selection');
            levelSection.style.transform = 'translateY(-100vh)';
            levelSection.style.opacity = '0';
            
            setTimeout(() => {
                levelSection.classList.add('hidden');
                // Show main content
                document.getElementById('main-content').classList.remove('hidden');
                document.getElementById('main-content').style.animation = 'slideUp 0.6s ease-out';
                
                // Update level header
                updateLevelHeader(level);
                
                // Initialize with assistant tab active
                showSection('assistant');
            }, 600);
        }
        
        function updateLevelHeader(level) {
            const levelData = {
                'ابتدائي': { icon: '🎒', title: 'الابتدائية', stats: '180+ درس متاح' },
                'إعدادي': { icon: '📚', title: 'الإعدادية', stats: '240+ درس متاح' }, 
                'ثانوي': { icon: '🎓', title: 'الثانوية', stats: '320+ درس متاح' }
            };
            
            const data = levelData[level];
            document.getElementById('level-icon').textContent = data.icon;
            document.getElementById('level-title').textContent = `المرحلة ${data.title}`;
            document.getElementById('level-stats').textContent = data.stats;
        }
        
        function goBackToLevelSelection() {
            // Hide main content
            document.getElementById('main-content').classList.add('hidden');
            
            // Show level selection screen
            const levelSection = document.getElementById('level-selection');
            levelSection.classList.remove('hidden');
            levelSection.style.transform = 'translateY(0)';
            levelSection.style.opacity = '1';
            
            // Reset selected level
            selectedLevel = '';
        }

        // Enhanced tab functionality
        function showSection(sectionName) {
            // Hide all sections with fade out
            document.querySelectorAll('.section-content').forEach(section => {
                section.style.opacity = '0';
                section.style.transform = 'translateY(20px)';
                setTimeout(() => section.classList.add('hidden'), 300);
            });
            
            // Remove active class from all tabs
            document.querySelectorAll('.tab-button').forEach(tab => {
                tab.classList.remove('active', 'bg-primary', 'text-white');
                tab.classList.add('hover:bg-gray-100', 'dark:hover:bg-gray-700');
            });
            
            // Show selected section with fade in
            setTimeout(() => {
                const targetSection = document.getElementById(`section-${sectionName}`);
                targetSection.classList.remove('hidden');
                targetSection.style.opacity = '1';
                targetSection.style.transform = 'translateY(0)';
                targetSection.style.transition = 'all 0.4s ease-out';
            }, 300);
            
            // Add active class to selected tab
            const activeTab = document.getElementById(`tab-${sectionName}`);
            activeTab.classList.add('active', 'bg-primary', 'text-white');
            activeTab.classList.remove('hover:bg-gray-100', 'dark:hover:bg-gray-700');
        }

        // Enhanced AI Assistant functionality
        function askQuestion(question) {
            document.getElementById('question-input').value = question;
            sendQuestion();
        }

        async function sendQuestion() {
            const questionInput = document.getElementById('question-input');
            const question = questionInput.value.trim();
            
            if (!question) {
                showNotification('خطأ', 'يرجى كتابة سؤال أولاً', 'error');
                return;
            }

            const responseDiv = document.getElementById('ai-response');
            const responseContent = document.getElementById('response-content');
            
            responseDiv.classList.remove('hidden');
            responseDiv.style.animation = 'slideDown 0.5s ease-out';
            responseContent.innerHTML = `
                <div class="text-center py-8">
                    <div class="animate-spin inline-block w-8 h-8 border-4 border-current border-t-transparent rounded-full text-primary"></div>
                    <div class="mt-4 text-lg font-medium typing-animation">جاري البحث عن أفضل إجابة</div>
                    <div class="mt-2 text-sm text-gray-600 dark:text-gray-400">قد يستغرق هذا بضع ثوانٍ...</div>
                </div>
            `;

            try {
                if (window.Poe) {
                    window.Poe.registerHandler('ai-tutor-handler', (result) => {
                        const message = result.responses[0];
                        if (message.status === 'error') {
                            responseContent.innerHTML = `
                                <div class="text-center py-8">
                                    <div class="text-4xl mb-4">❌</div>
                                    <div class="text-red-600 font-medium">حدث خطأ: ${message.statusText || 'لم نتمكن من الحصول على إجابة'}</div>
                                    <button onclick="sendQuestion()" class="mt-4 px-4 py-2 bg-primary text-white rounded-lg hover:bg-primary/90 transition-colors">إعادة المحاولة</button>
                                </div>
                            `;
                        } else if (message.status === 'incomplete') {
                            responseContent.innerHTML = `
                                <div class="prose dark:prose-invert max-w-none">
                                    ${message.content}
                                    <div class="mt-4 text-sm text-blue-600 dark:text-blue-400 flex items-center space-x-2">
                                        <div class="animate-pulse w-2 h-2 bg-blue-600 rounded-full"></div>
                                        <span>جاري الكتابة...</span>
                                    </div>
                                </div>
                            `;
                        } else if (message.status === 'complete') {
                            responseContent.innerHTML = `
                                <div class="prose dark:prose-invert max-w-none">
                                    ${message.content}
                                </div>
                            `;
                        }
                    });

                    await window.Poe.sendUserMessage(
                        `@Claude-Sonnet-4 أنت مساعد تعليمي ذكي متخصص في المناهج العربية. أجب على السؤال التالي بطريقة واضحة ومفصلة مناسبة للطلاب مع تقديم أمثلة تطبيقية: ${question}`,
                        {
                            handler: 'ai-tutor-handler',
                            stream: true,
                            openChat: false
                        }
                    );
                } else {
                    // Enhanced fallback response
                    setTimeout(() => {
                        responseContent.innerHTML = `
                            <div class="space-y-4">
                                <h4 class="font-bold text-xl flex items-center space-x-2">
                                    <span>🎯</span><span>إجابة على: ${question}</span>
                                </h4>
                                <div class="bg-yellow-50 dark:bg-yellow-900/20 border border-yellow-200 dark:border-yellow-800 rounded-xl p-4">
                                    <p class="text-yellow-800 dark:text-yellow-200">
                                        هذا مثال على إجابة المساعد الذكي. في التطبيق الحقيقي، سيتم الاتصال بنموذج الذكاء الاصطناعي للحصول على إجابة دقيقة ومفصلة مخصصة لسؤالك.
                                    </p>
                                </div>
                                <div class="bg-blue-50 dark:bg-blue-900/20 border border-blue-200 dark:border-blue-800 rounded-xl p-4">
                                    <h5 class="font-bold mb-2">مميزات الإجابة الذكية:</h5>
                                    <ul class="text-sm space-y-1">
                                        <li>• شرح مفصل ومبسط</li>
                                        <li>• أمثلة تطبيقية من الحياة الواقعية</li>
                                        <li>• خطوات الحل واضحة ومرتبة</li>
                                        <li>• مصادر إضافية للتعلم</li>
                                    </ul>
                                </div>
                            </div>
                        `;
                    }, 2000);
                }
            } catch (error) {
                responseContent.innerHTML = `
                    <div class="text-center py-8">
                        <div class="text-4xl mb-4">⚠️</div>
                        <div class="text-red-600 font-medium">حدث خطأ في الاتصال</div>
                        <div class="text-sm text-gray-600 dark:text-gray-400 mt-2">يرجى التحقق من الاتصال والمحاولة مرة أخرى</div>
                        <button onclick="sendQuestion()" class="mt-4 px-4 py-2 bg-primary text-white rounded-lg hover:bg-primary/90 transition-colors">إعادة المحاولة</button>
                    </div>
                `;
            }

            questionInput.value = '';
        }

        // Response interaction functions
        function likeResponse() {
            showNotification('شكراً!', 'تم تسجيل تقييمك الإيجابي', 'success');
        }

        function shareResponse() {
            showNotification('تم النسخ!', 'تم نسخ الإجابة للحافظة', 'info');
        }

        function saveResponse() {
            showNotification('تم الحفظ!', 'تم حفظ الإجابة في مفضلتك', 'success');
        }

        // Enhanced exam generation
        async function generateExam() {
            const subject = document.querySelector('#section-exams select:nth-of-type(1)').value;
            const level = document.querySelector('#section-exams select:nth-of-type(2)').value;
            const difficulty = document.querySelector('#section-exams select:nth-of-type(3)').value;
            const examType = document.querySelector('#section-exams select:nth-of-type(4)').value;
            const duration = document.querySelector('#section-exams select:nth-of-type(5)').value;
            const questionCount = document.getElementById('question-count').value;

            showNotification('جاري الإنشاء...', 'يتم إنشاء امتحان مخصص لك', 'info');

            try {
                if (window.Poe) {
                    window.Poe.registerHandler('exam-generator-handler', (result) => {
                        const message = result.responses[0];
                        if (message.status === 'complete') {
                            showExamModal(message.content, subject, level, duration);
                            showNotification('تم بنجاح!', 'تم إنشاء الامتحان بنجاح', 'success');
                        }
                    });

                    await window.Poe.sendUserMessage(
                        `@Claude-Sonnet-4 أنشئ ${examType} في مادة ${subject} للمستوى ${level} بصعوبة ${difficulty} لمدة ${duration} يحتوي على ${questionCount} سؤال متنوع. يجب أن يتضمن الامتحان أسئلة اختيار متعدد، أسئلة مقالية قصيرة، وأسئلة تطبيقية. قدم الإجابات النموذجية وسلم التقييم أيضاً.`,
                        {
                            handler: 'exam-generator-handler',
                            stream: false,
                            openChat: false
                        }
                    );
                } else {
                    // Enhanced fallback
                    setTimeout(() => {
                        const sampleExam = `امتحان ${subject} - ${level}\nالمدة: ${duration}\nعدد الأسئلة: ${questionCount}\n\n=== الجزء الأول: اختيار متعدد ===\n\nالسؤال 1: [سؤال نموذجي]\nأ) خيار 1\nب) خيار 2\nج) خيار 3\nد) خيار 4\n\nالسؤال 2: [سؤال نموذجي]\n...\n\n=== الجزء الثاني: أسئلة مقالية ===\n\nالسؤال 5: [سؤال تطبيقي]\n\n=== الإجابات النموذجية ===\n\n1. الإجابة الصحيحة: ج\n2. الإجابة الصحيحة: أ\n...`;
                        showExamModal(sampleExam, subject, level, duration);
                        showNotification('تم بنجاح!', 'تم إنشاء امتحان نموذجي', 'success');
                    }, 3000);
                }
            } catch (error) {
                showNotification('خطأ!', 'حدث خطأ في إنشاء الامتحان', 'error');
            }
        }

        function showExamModal(examContent, subject, level, duration) {
            const modal = document.createElement('div');
            modal.className = 'fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50 p-4';
            modal.innerHTML = `
                <div class="bg-white dark:bg-gray-800 rounded-2xl shadow-2xl max-w-6xl w-full max-h-[90vh] overflow-hidden animate-scale-in">
                    <div class="bg-gradient-to-r from-primary to-purple-600 text-white p-6">
                        <div class="flex justify-between items-center">
                            <div>
                                <h3 class="text-2xl font-bold">امتحان ${subject} - ${level}</h3>
                                <p class="opacity-90">المدة: ${duration}</p>
                            </div>
                            <button onclick="this.closest('.fixed').remove()" class="text-white hover:text-gray-200 transition-colors">
                                <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                                </svg>
                            </button>
                        </div>
                    </div>
                    <div class="p-6 overflow-y-auto custom-scrollbar max-h-[60vh]">
                        <div class="prose dark:prose-invert max-w-none">
                            <pre class="whitespace-pre-wrap text-sm leading-relaxed">${examContent}</pre>
                        </div>
                    </div>
                    <div class="border-t border-gray-200 dark:border-gray-700 p-6 bg-gray-50 dark:bg-gray-900">
                        <div class="flex justify-between items-center">
                            <div class="flex space-x-3">
                                <button onclick="startExam()" class="px-6 py-3 bg-green-500 text-white rounded-xl hover:bg-green-600 transition-colors font-medium">
                                    🚀 بدء الامتحان
                                </button>
                                <button onclick="downloadExam('${examContent.replace(/'/g, "\\'")}', '${subject}-${level}')" class="px-6 py-3 bg-blue-500 text-white rounded-xl hover:bg-blue-600 transition-colors font-medium">
                                    📄 تحميل PDF
                                </button>
                            </div>
                            <button onclick="this.closest('.fixed').remove()" class="px-6 py-3 text-gray-600 dark:text-gray-400 hover:bg-gray-100 dark:hover:bg-gray-700 rounded-xl transition-colors">
                                إغلاق
                            </button>
                        </div>
                    </div>
                </div>
            `;
            document.body.appendChild(modal);
        }

        function startExam() {
            showNotification('بدء الامتحان!', 'سيتم توجيهك لصفحة الامتحان', 'info');
            // يمكن إضافة منطق بدء الامتحان هنا
        }

        function downloadExam(content, filename) {
            const blob = new Blob([content], { type: 'text/plain;charset=utf-8' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = `${filename}-امتحان.txt`;
            a.click();
            URL.revokeObjectURL(url);
            showNotification('تم التحميل!', 'تم تحميل الامتحان بنجاح', 'success');
        }

        // Enhanced notification system
        function showNotification(title, message, type = 'success') {
            const notification = document.getElementById('notification');
            const titleElement = document.getElementById('notification-title');
            const messageElement = document.getElementById('notification-message');
            
            const icons = {
                success: '✅',
                error: '❌',
                warning: '⚠️',
                info: 'ℹ️'
            };
            
            const colors = {
                success: 'border-green-200 dark:border-green-800',
                error: 'border-red-200 dark:border-red-800',
                warning: 'border-yellow-200 dark:border-yellow-800',
                info: 'border-blue-200 dark:border-blue-800'
            };
            
            notification.className = `fixed top-24 left-4 bg-white dark:bg-gray-800 shadow-xl rounded-xl p-4 notification z-50 border ${colors[type]}`;
            notification.querySelector('.text-2xl').textContent = icons[type];
            titleElement.textContent = title;
            messageElement.textContent = message;
            
            notification.classList.add('show');
            
            setTimeout(() => {
                notification.classList.remove('show');
            }, 4000);
        }

        // Enter key support for question input
        document.getElementById('question-input').addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                sendQuestion();
            }
        });

        // Close mobile menu when clicking outside
        document.addEventListener('click', function(e) {
            const menu = document.getElementById('mobile-menu');
            const menuButton = document.querySelector('button[onclick="toggleMobileMenu()"]');
            
            if (!menu.contains(e.target) && !menuButton.contains(e.target)) {
                menu.classList.add('translate-x-full');
            }
        });

        // Enhanced Exams Database
        const examsDatabase = [
            {
                id: 1,
                title: "فرض في المعادلات التربيعية",
                subject: "رياضيات",
                level: "ثانوي",
                type: "فرض محروس",
                duration: "ساعة واحدة",
                questions: 20,
                views: 1563,
                rating: 4.8,
                date: "منذ يومين",
                difficulty: "متوسط",
                source: "وزارة التربية الوطنية",
                content: `امتحان الرياضيات - المعادلات التربيعية
المدة: ساعة واحدة
عدد الأسئلة: 20

=== الجزء الأول: أسئلة الاختيار من متعدد ===

السؤال 1: ما هي الصيغة العامة للمعادلة التربيعية؟
أ) ax + b = 0
ب) ax² + bx + c = 0
ج) ax³ + bx² + c = 0
د) ax² + c = 0

السؤال 2: قيمة المميز للمعادلة x² - 6x + 9 = 0 هي:
أ) 0
ب) 36
ج) -36
د) 18

=== الجزء الثاني: أسئلة مقالية ===

السؤال 11: حل المعادلة التربيعية التالية: x² - 5x + 6 = 0

السؤال 12: أوجد قيم x التي تحقق المعادلة: 2x² + 7x - 4 = 0

=== الجزء الثالث: مسائل تطبيقية ===

السؤال 16: مستطيل طوله يزيد عن عرضه بـ 3 متر، إذا كان حجمه 40 متر مربع، أوجد أبعاده.

=== الإجابات النموذجية ===
1. ب) ax² + bx + c = 0
2. أ) 0
11. x = 2 أو x = 3
12. x = 0.5 أو x = -4
16. العرض = 5 متر، الطول = 8 متر`
            },
            {
                id: 2,
                title: "امتحان قوانين نيوتن للحركة",
                subject: "فيزياء",
                level: "ثانوي",
                type: "امتحان فصلي",
                duration: "ساعتان",
                questions: 25,
                views: 2847,
                rating: 4.9,
                date: "منذ أسبوع",
                difficulty: "متقدم",
                source: "المركز الوطني للامتحانات",
                content: `امتحان الفيزياء - قوانين نيوتن للحركة
المدة: ساعتان
عدد الأسئلة: 25

=== الجزء الأول: النظرية ===

السؤال 1: اذكر نص قانون نيوتن الأول وأعط مثالاً عليه.

السؤال 2: ما المقصود بالقصور الذاتي؟

=== الجزء الثاني: التطبيقات ===

السؤال 10: جسم كتلته 5 كيلوغرام يتحرك بسرعة 10 م/ث، أوجد كمية الحركة.

السؤال 15: قوة قدرها 20 نيوتن تؤثر على جسم كتلته 4 كيلوغرام، احسب التسارع.

=== الجزء الثالث: مسائل متقدمة ===

السؤال 20: سيارة كتلتها 1200 كيلوغرام تتحرك بسرعة 60 كم/ساعة، أوجد القوة اللازمة لإيقافها في مسافة 50 متر.`
            },
            {
                id: 3,
                title: "تمارين في الكيمياء العضوية",
                subject: "كيمياء",
                level: "ثانوي",
                type: "تمارين تطبيقية",
                duration: "45 دقيقة",
                questions: 15,
                views: 1234,
                rating: 4.6,
                date: "منذ 3 أيام",
                difficulty: "سهل",
                source: "دار النشر العلمية",
                content: `تمارين الكيمياء العضوية
المدة: 45 دقيقة
عدد الأسئلة: 15

=== التمرين الأول: المركبات الهيدروكربونية ===

1. ما هي الصيغة الجزيئية للميثان؟
2. اكتب الصيغة البنائية للإيثان.
3. ما الفرق بين الألكان والألكين؟

=== التمرين الثاني: التفاعلات ===

10. اكتب معادلة احتراق الميثان.
11. ما نواتج تفاعل الإيثيلين مع الماء؟

=== التمرين الثالث: التسمية ===

13. اذكر اسم المركب: CH₃-CH₂-CH₃
14. ما اسم المركب الذي صيغته C₄H₁₀؟`
            },
            {
                id: 4,
                title: "فرض في النحو العربي - الإعراب",
                subject: "لغة عربية",
                level: "إعدادي",
                type: "فرض محروس",
                duration: "ساعة واحدة",
                questions: 18,
                views: 1876,
                rating: 4.7,
                date: "منذ 5 أيام",
                difficulty: "متوسط",
                source: "أكاديمية التربية والتكوين",
                content: `فرض في النحو العربي - الإعراب
المدة: ساعة واحدة
عدد الأسئلة: 18

=== الجزء الأول: الإعراب ===

أعرب ما تحته خط:
1. "يحب الطلاب المدرسة"
2. "قرأت كتاباً مفيداً"
3. "سافر أحمد إلى مكة"

=== الجزء الثاني: القواعد ===

4. ما أنواع الخبر في الجملة الاسمية؟
5. متى يُرفع المفعول به؟
6. اذكر علامات الإعراب الأصلية.

=== الجزء الثالث: التطبيق ===

10. حول الجملة الفعلية إلى اسمية: "يلعب الأطفال في الحديقة"
11. استخرج المبتدأ والخبر: "العلم نور يضيء الطريق"`
            },
            {
                id: 5,
                title: "امتحان علوم الحياة والأرض - الخلية",
                subject: "علوم الحياة والأرض",
                level: "إعدادي",
                type: "امتحان فصلي",
                duration: "ساعة ونصف",
                questions: 22,
                views: 2156,
                rating: 4.8,
                date: "منذ أسبوعين",
                difficulty: "متوسط",
                source: "وزارة التربية الوطنية",
                content: `امتحان علوم الحياة والأرض - الخلية
المدة: ساعة ونصف
عدد الأسئلة: 22

=== الجزء الأول: التعريفات ===

1. عرّف الخلية.
2. ما الفرق بين الخلية النباتية والحيوانية؟
3. اذكر وظائف النواة.

=== الجزء الثاني: أجزاء الخلية ===

10. اذكر مكونات الغشاء الخلوي.
11. ما وظيفة الميتوكوندريا؟
12. أين توجد الكلوروفيل في الخلية النباتية؟

=== الجزء الثالث: الوظائف ===

18. اشرح عملية التنفس الخلوي.
19. ما أهمية عملية التمثيل الضوئي؟
20. كيف تنقسم الخلايا؟`
            },
            {
                id: 6,
                title: "فرض في تاريخ المغرب المعاصر",
                subject: "اجتماعيات",
                level: "ثانوي",
                type: "فرض محروس",
                duration: "ساعتان",
                questions: 16,
                views: 1654,
                rating: 4.5,
                date: "منذ 4 أيام",
                difficulty: "متقدم",
                source: "المديرية الإقليمية للتعليم",
                content: `فرض في تاريخ المغرب المعاصر
المدة: ساعتان
عدد الأسئلة: 16

=== الجزء الأول: الحقبة الاستعمارية ===

1. متى بدأت الحماية الفرنسية على المغرب؟
2. من كان أول مقيم عام فرنسي في المغرب؟
3. اذكر أهم بنود معاهدة فاس.

=== الجزء الثاني: المقاومة المغربية ===

8. من هو عبد الكريم الخطابي؟
9. ما أهمية معركة أنوال؟
10. اذكر أهم قادة المقاومة في الأطلس.

=== الجزء الثالث: الاستقلال ===

13. متى حصل المغرب على استقلاله؟
14. من كان ملك المغرب عند الاستقلال؟
15. ما أهمية عودة الملك محمد الخامس من المنفى؟`
            },
            {
                id: 7,
                title: "تمارين في الإنجليزية - Grammar",
                subject: "لغة إنجليزية",
                level: "ثانوي",
                type: "تمارين تطبيقية",
                duration: "ساعة واحدة",
                questions: 20,
                views: 1987,
                rating: 4.4,
                date: "منذ يوم واحد",
                difficulty: "متوسط",
                source: "Cambridge Educational",
                content: `English Grammar Exercises
Duration: One Hour
Number of Questions: 20

=== Part I: Tenses ===

1. Choose the correct tense: "I _____ (study) English for 5 years."
   a) study  b) studied  c) have studied  d) am studying

2. Complete: "When I arrived, they _____ dinner."
   a) had  b) were having  c) have had  d) had had

=== Part II: Conditional Sentences ===

10. "If I _____ rich, I would travel the world."
    a) am  b) was  c) were  d) will be

11. Complete: "If you study hard, you _____ pass the exam."
    a) will  b) would  c) can  d) could

=== Part III: Vocabulary ===

15. Choose the synonym of "beautiful":
    a) ugly  b) gorgeous  c) bad  d) small

16. What's the opposite of "ancient"?
    a) old  b) modern  c) big  d) small`
            },
            {
                id: 8,
                title: "امتحان الرياضيات للمرحلة الابتدائية",
                subject: "رياضيات",
                level: "ابتدائي",
                type: "امتحان فصلي",
                duration: "ساعة واحدة",
                questions: 15,
                views: 987,
                rating: 4.9,
                date: "منذ 3 أيام",
                difficulty: "سهل",
                source: "مديرية التعليم الابتدائي",
                content: `امتحان الرياضيات - المرحلة الابتدائية
المدة: ساعة واحدة
عدد الأسئلة: 15

=== الجزء الأول: العمليات الحسابية ===

1. احسب: 25 + 17 = ?
2. احسب: 84 - 36 = ?
3. احسب: 12 × 8 = ?
4. احسب: 144 ÷ 12 = ?

=== الجزء الثاني: الكسور ===

8. ما هو نصف العدد 20؟
9. احسب: 1/4 + 1/4 = ?
10. أيهما أكبر: 1/2 أم 1/3؟

=== الجزء الثالث: الهندسة ===

12. كم ضلعاً للمثلث؟
13. ما اسم الشكل الذي له 4 أضلاع متساوية؟
14. احسب محيط مربع ضلعه 5 سم.`
            }
        ];

        let currentExamsView = 'filtered';
        let currentPage = 1;
        const examsPerPage = 6;

        // Load and display exams
        function loadExams() {
            const container = document.getElementById('exams-container');
            if (!container) return;

            const filtered = filterExamsList();
            const startIndex = (currentPage - 1) * examsPerPage;
            const endIndex = startIndex + examsPerPage;
            const examsToShow = filtered.slice(0, endIndex);

            container.innerHTML = '';

            examsToShow.forEach((exam, index) => {
                const examCard = createExamCard(exam, index);
                container.appendChild(examCard);
            });

            // Update load more button
            const loadMoreBtn = document.getElementById('load-more-btn');
            if (loadMoreBtn) {
                if (endIndex >= filtered.length) {
                    loadMoreBtn.style.display = 'none';
                } else {
                    loadMoreBtn.style.display = 'block';
                    loadMoreBtn.textContent = `تحميل المزيد (${filtered.length - endIndex} متبقي)`;
                }
            }
        }

        function filterExamsList() {
            const subjectFilter = document.getElementById('exam-subject-filter')?.value || 'all';
            const levelFilter = document.getElementById('exam-level-filter')?.value || 'all';
            const searchTerm = document.getElementById('exam-search')?.value.toLowerCase() || '';

            return examsDatabase.filter(exam => {
                const matchesSubject = subjectFilter === 'all' || exam.subject === subjectFilter;
                const matchesLevel = levelFilter === 'all' || exam.level === levelFilter;
                const matchesSearch = searchTerm === '' || 
                    exam.title.toLowerCase().includes(searchTerm) ||
                    exam.subject.toLowerCase().includes(searchTerm);

                return matchesSubject && matchesLevel && matchesSearch;
            });
        }

        function createExamCard(exam, index) {
            const card = document.createElement('div');
            card.className = 'border border-gray-200 dark:border-gray-600 rounded-xl p-4 hover:shadow-lg transition-all transform hover:scale-102 animate-fade-in';
            card.style.animationDelay = `${index * 0.1}s`;

            const difficultyColors = {
                'سهل': 'bg-green-500',
                'متوسط': 'bg-yellow-500',
                'متقدم': 'bg-red-500',
                'صعب': 'bg-purple-500'
            };

            const subjectColors = {
                'رياضيات': 'bg-blue-500',
                'فيزياء': 'bg-purple-500',
                'كيمياء': 'bg-orange-500',
                'علوم الحياة والأرض': 'bg-green-600',
                'لغة عربية': 'bg-red-500',
                'لغة إنجليزية': 'bg-indigo-500',
                'لغة فرنسية': 'bg-pink-500',
                'اجتماعيات': 'bg-teal-500'
            };

            card.innerHTML = `
                <div class="flex items-center justify-between mb-3">
                    <h5 class="font-bold text-lg text-gray-800 dark:text-gray-200">${exam.title}</h5>
                    <div class="flex space-x-2">
                        <span class="text-xs ${subjectColors[exam.subject] || 'bg-gray-500'} text-white px-2 py-1 rounded-full">${exam.subject}</span>
                        <span class="text-xs ${difficultyColors[exam.difficulty] || 'bg-gray-500'} text-white px-2 py-1 rounded-full">${exam.difficulty}</span>
                    </div>
                </div>
                <p class="text-sm text-gray-600 dark:text-gray-400 mb-3">${exam.type} - ${exam.duration} - ${exam.questions} سؤال</p>
                <div class="grid grid-cols-2 gap-2 text-xs text-gray-500 dark:text-gray-400 mb-3">
                    <span class="flex items-center space-x-1">
                        <span>📅</span><span>${exam.date}</span>
                    </span>
                    <span class="flex items-center space-x-1">
                        <span>👁️</span><span>${exam.views} مشاهدة</span>
                    </span>
                    <span class="flex items-center space-x-1">
                        <span>⭐</span><span>${exam.rating} تقييم</span>
                    </span>
                    <span class="flex items-center space-x-1">
                        <span>🎓</span><span>${exam.level}</span>
                    </span>
                </div>
                <div class="text-xs text-gray-400 mb-3">
                    <span>📚 المصدر: ${exam.source}</span>
                </div>
                <div class="flex space-x-2">
                    <button onclick="showExamModal('${exam.content.replace(/'/g, "\\'")}', '${exam.subject}', '${exam.level}', '${exam.duration}')" class="flex-1 px-3 py-2 bg-blue-500 text-white rounded-lg text-sm hover:bg-blue-600 transition-colors font-medium">
                        🚀 بدء الامتحان
                    </button>
                    <button onclick="downloadExam('${exam.content.replace(/'/g, "\\'")}', '${exam.title}')" class="px-3 py-2 bg-green-500 text-white rounded-lg text-sm hover:bg-green-600 transition-colors">
                        📄 PDF
                    </button>
                    <button onclick="saveExam(${exam.id})" class="px-3 py-2 border border-gray-300 dark:border-gray-600 rounded-lg text-sm hover:bg-gray-100 dark:hover:bg-gray-600 transition-colors">
                        🔖
                    </button>
                </div>
            `;

            return card;
        }

        function filterExams() {
            currentPage = 1;
            loadExams();
        }

        function loadMoreExams() {
            currentPage++;
            loadExams();
        }

        function toggleExamView() {
            const toggleBtn = document.getElementById('view-toggle-text');
            if (currentExamsView === 'filtered') {
                currentExamsView = 'all';
                toggleBtn.textContent = '🔍 عرض مفلتر';
                // Show all exams without pagination
                const container = document.getElementById('exams-container');
                container.innerHTML = '';
                examsDatabase.forEach((exam, index) => {
                    const examCard = createExamCard(exam, index);
                    container.appendChild(examCard);
                });
                document.getElementById('load-more-btn').style.display = 'none';
            } else {
                currentExamsView = 'filtered';
                toggleBtn.textContent = '🔍 عرض الكل';
                currentPage = 1;
                loadExams();
            }
        }

        function saveExam(examId) {
            const exam = examsDatabase.find(e => e.id === examId);
            if (exam) {
                showNotification('تم الحفظ!', `تم حفظ امتحان "${exam.title}" في مفضلتك`, 'success');
            }
        }

        // Import Modal Functions
        function showImportModal() {
            const modal = document.createElement('div');
            modal.className = 'fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50 p-4';
            modal.innerHTML = `
                <div class="bg-white dark:bg-gray-800 rounded-2xl shadow-2xl max-w-4xl w-full max-h-[90vh] overflow-hidden animate-scale-in">
                    <div class="bg-gradient-to-r from-purple-500 to-pink-600 text-white p-6">
                        <div class="flex justify-between items-center">
                            <div>
                                <h3 class="text-2xl font-bold">استيراد امتحانات من مصادر خارجية</h3>
                                <p class="opacity-90">أضف امتحانات من مواقع تعليمية أو ملفات محلية</p>
                            </div>
                            <button onclick="this.closest('.fixed').remove()" class="text-white hover:text-gray-200 transition-colors">
                                <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                                </svg>
                            </button>
                        </div>
                    </div>
                    <div class="p-6">
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                            <!-- Upload File Section -->
                            <div class="border-2 border-dashed border-gray-300 dark:border-gray-600 rounded-xl p-6 text-center">
                                <div class="text-4xl mb-4">📁</div>
                                <h4 class="text-lg font-bold mb-2">رفع ملف امتحان</h4>
                                <p class="text-sm text-gray-600 dark:text-gray-400 mb-4">ادعم الملفات: PDF, DOC, TXT</p>
                                <input type="file" id="exam-file-input" accept=".pdf,.doc,.docx,.txt" class="hidden">
                                <button onclick="document.getElementById('exam-file-input').click()" class="px-6 py-3 bg-blue-500 text-white rounded-lg hover:bg-blue-600 transition-colors">
                                    اختيار ملف
                                </button>
                            </div>
                            
                            <!-- Text Import Section -->
                            <div class="border border-gray-300 dark:border-gray-600 rounded-xl p-6">
                                <h4 class="text-lg font-bold mb-4 flex items-center space-x-2">
                                    <span>📝</span><span>استيراد من النص</span>
                                </h4>
                                <textarea id="import-text-area" placeholder="الصق محتوى الامتحان هنا..." class="w-full h-40 p-3 border border-gray-300 dark:border-gray-600 rounded-lg dark:bg-gray-700 text-sm resize-none"></textarea>
                                <button onclick="importFromText()" class="mt-4 w-full px-6 py-3 bg-green-500 text-white rounded-lg hover:bg-green-600 transition-colors">
                                    استيراد النص
                                </button>
                            </div>
                        </div>
                        
                        <!-- Popular Sources Section -->
                        <div class="mt-8">
                            <h4 class="text-lg font-bold mb-4">مصادر شائعة للامتحانات</h4>
                            <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                                <button onclick="importFromSource('وزارة التربية الوطنية')" class="p-4 border border-gray-300 dark:border-gray-600 rounded-lg hover:bg-gray-50 dark:hover:bg-gray-700 transition-colors">
                                    <div class="text-2xl mb-2">🏛️</div>
                                    <div class="font-medium">وزارة التربية الوطنية</div>
                                    <div class="text-xs text-gray-500">امتحانات رسمية</div>
                                </button>
                                <button onclick="importFromSource('المركز الوطني للامتحانات')" class="p-4 border border-gray-300 dark:border-gray-600 rounded-lg hover:bg-gray-50 dark:hover:bg-gray-700 transition-colors">
                                    <div class="text-2xl mb-2">🎯</div>
                                    <div class="font-medium">المركز الوطني للامتحانات</div>
                                    <div class="text-xs text-gray-500">اختبارات معيارية</div>
                                </button>
                                <button onclick="importFromSource('دور النشر التعليمية')" class="p-4 border border-gray-300 dark:border-gray-600 rounded-lg hover:bg-gray-50 dark:hover:bg-gray-700 transition-colors">
                                    <div class="text-2xl mb-2">📚</div>
                                    <div class="font-medium">دور النشر التعليمية</div>
                                    <div class="text-xs text-gray-500">كتب مدرسية</div>
                                </button>
                            </div>
                        </div>
                    </div>
                    <div class="border-t border-gray-200 dark:border-gray-700 p-6 bg-gray-50 dark:bg-gray-900">
                        <div class="flex justify-end space-x-3">
                            <button onclick="this.closest('.fixed').remove()" class="px-6 py-3 text-gray-600 dark:text-gray-400 hover:bg-gray-100 dark:hover:bg-gray-700 rounded-xl transition-colors">
                                إغلاق
                            </button>
                            <button onclick="saveImportedExam()" class="px-6 py-3 bg-primary text-white rounded-xl hover:bg-primary/90 transition-colors">
                                حفظ الامتحان المستورد
                            </button>
                        </div>
                    </div>
                </div>
            `;
            document.body.appendChild(modal);

            // Handle file input change
            document.getElementById('exam-file-input').addEventListener('change', function(e) {
                const file = e.target.files[0];
                if (file) {
                    handleFileImport(file);
                }
            });
        }

        function handleFileImport(file) {
            const reader = new FileReader();
            reader.onload = function(e) {
                const content = e.target.result;
                document.getElementById('import-text-area').value = content;
                showNotification('تم تحميل الملف!', `تم تحميل "${file.name}" بنجاح`, 'success');
            };
            reader.readAsText(file);
        }

        function importFromText() {
            const text = document.getElementById('import-text-area').value.trim();
            if (!text) {
                showNotification('خطأ!', 'يرجى إدخال محتوى الامتحان', 'error');
                return;
            }
            
            // Create new exam object
            const newExam = {
                id: examsDatabase.length + 1,
                title: "امتحان مستورد - " + new Date().toLocaleDateString('ar'),
                subject: "متنوع",
                level: selectedLevel || "عام",
                type: "امتحان مستورد",
                duration: "غير محدد",
                questions: (text.match(/سؤال|السؤال/g) || []).length,
                views: 0,
                rating: 0,
                date: "الآن",
                difficulty: "متوسط",
                source: "مستورد من المستخدم",
                content: text
            };
            
            examsDatabase.push(newExam);
            loadExams();
            showNotification('تم الاستيراد!', 'تم استيراد الامتحان بنجاح', 'success');
        }

        function importFromSource(source) {
            showNotification('جاري التحميل...', `جاري جلب امتحانات من ${source}`, 'info');
            
            // Simulate fetching from external source
            setTimeout(() => {
                const sampleExams = [
                    {
                        title: `امتحان من ${source} - الرياضيات`,
                        subject: "رياضيات",
                        content: `امتحان رسمي من ${source}\n\nالسؤال الأول: حل المعادلة...\nالسؤال الثاني: أوجد قيمة...\n\nهذا امتحان نموذجي تم جلبه من المصدر الخارجي.`
                    },
                    {
                        title: `امتحان من ${source} - العلوم`,
                        subject: "علوم الحياة والأرض",
                        content: `امتحان رسمي من ${source}\n\nالسؤال الأول: عرّف الخلية...\nالسؤال الثاني: اذكر وظائف...\n\nهذا امتحان نموذجي تم جلبه من المصدر الخارجي.`
                    }
                ];
                
                sampleExams.forEach((exam, index) => {
                    const newExam = {
                        id: examsDatabase.length + 1 + index,
                        title: exam.title,
                        subject: exam.subject,
                        level: selectedLevel || "عام",
                        type: "امتحان رسمي",
                        duration: "ساعة واحدة",
                        questions: 20,
                        views: Math.floor(Math.random() * 1000),
                        rating: (4 + Math.random()).toFixed(1),
                        date: "الآن",
                        difficulty: "متوسط",
                        source: source,
                        content: exam.content
                    };
                    examsDatabase.push(newExam);
                });
                
                loadExams();
                showNotification('تم بنجاح!', `تم استيراد ${sampleExams.length} امتحان من ${source}`, 'success');
            }, 2000);
        }

        function saveImportedExam() {
            showNotification('تم الحفظ!', 'تم حفظ جميع الامتحانات المستوردة', 'success');
            // Close modal
            document.querySelector('.fixed').remove();
        }

        // Initialize exams when page loads
        document.addEventListener('DOMContentLoaded', function() {
            // Add floating animation to elements
            const floatingElements = document.querySelectorAll('.animate-float');
            floatingElements.forEach((el, index) => {
                el.style.animationDelay = `${index * 0.5}s`;
            });

            // Load exams when exams section is shown
            setTimeout(() => {
                loadExams();
            }, 1000);
        });
    </script>
</body>
</html>
