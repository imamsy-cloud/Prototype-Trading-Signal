<!DOCTYPE html>
<html lang="en" class="light">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SignalMax - Admin Dashboard</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        primary: {
                            '50': '#f0fdf4',
                            '100': '#dcfce7',
                            '200': '#bbf7d0',
                            '300': '#86efac',
                            '400': '#4ade80',
                            '500': '#22c55e',
                            '600': '#16a34a',
                            '700': '#15803d',
                            '800': '#166534',
                            '900': '#14532d',
                            '950': '#052e16',
                        },
                    }
                }
            }
        }
    </script>
    <style>
        body {
            font-family: 'Inter', sans-serif;
        }
        .admin-page {
            display: none;
        }
        .admin-page.active {
            display: block;
        }
        .sidebar-link.active {
            background-color: #16a34a; /* primary-600 */
            color: white;
        }
        .sidebar-link.active i {
            color: white;
        }
    </style>
</head>
<body class="bg-gray-100 dark:bg-gray-900 text-gray-800 dark:text-gray-200">

    <div class="flex h-screen">
        <!-- Sidebar -->
        <aside class="w-64 bg-white dark:bg-gray-800 shadow-md flex-shrink-0 flex flex-col">
            <div class="h-16 flex items-center justify-center border-b dark:border-gray-700">
                <i class="fas fa-chart-line text-2xl text-primary-500"></i>
                <h1 class="text-xl font-bold ml-2">SignalMax</h1>
            </div>
            <nav class="flex-1 px-4 py-6 space-y-2">
                <a href="#" data-target="page-dashboard" class="sidebar-link active flex items-center px-4 py-2 rounded-lg text-gray-700 dark:text-gray-300 hover:bg-primary-500 hover:text-white">
                    <i class="fas fa-tachometer-alt w-6 text-primary-500"></i>
                    <span>Dashboard</span>
                </a>
                <a href="#" data-target="page-users" class="sidebar-link flex items-center px-4 py-2 rounded-lg text-gray-700 dark:text-gray-300 hover:bg-primary-500 hover:text-white">
                    <i class="fas fa-users w-6 text-primary-500"></i>
                    <span>Manajemen User</span>
                </a>
                <a href="#" data-target="page-signals" class="sidebar-link flex items-center px-4 py-2 rounded-lg text-gray-700 dark:text-gray-300 hover:bg-primary-500 hover:text-white">
                    <i class="fas fa-signal w-6 text-primary-500"></i>
                    <span>Manajemen Sinyal</span>
                </a>
                <a href="#" data-target="page-content" class="sidebar-link flex items-center px-4 py-2 rounded-lg text-gray-700 dark:text-gray-300 hover:bg-primary-500 hover:text-white">
                    <i class="fas fa-book-open w-6 text-primary-500"></i>
                    <span>Manajemen Konten</span>
                </a>
                <a href="#" data-target="page-events" class="sidebar-link flex items-center px-4 py-2 rounded-lg text-gray-700 dark:text-gray-300 hover:bg-primary-500 hover:text-white">
                    <i class="fas fa-calendar-alt w-6 text-primary-500"></i>
                    <span>Manajemen Event</span>
                </a>
                 <a href="#" data-target="page-payments" class="sidebar-link flex items-center px-4 py-2 rounded-lg text-gray-700 dark:text-gray-300 hover:bg-primary-500 hover:text-white">
                    <i class="fas fa-receipt w-6 text-primary-500"></i>
                    <span>Pembayaran Manual</span>
                </a>
                <a href="#" data-target="page-settings" class="sidebar-link flex items-center px-4 py-2 rounded-lg text-gray-700 dark:text-gray-300 hover:bg-primary-500 hover:text-white">
                    <i class="fas fa-cog w-6 text-primary-500"></i>
                    <span>Pengaturan</span>
                </a>
            </nav>
            <div class="p-4 border-t dark:border-gray-700">
                 <a href="#" class="flex items-center px-4 py-2 rounded-lg text-red-500 hover:bg-red-100 dark:hover:bg-red-900/50">
                    <i class="fas fa-sign-out-alt w-6"></i>
                    <span>Logout</span>
                </a>
            </div>
        </aside>

        <!-- Main Content -->
        <main class="flex-1 flex flex-col overflow-hidden">
            <!-- Header -->
            <header class="h-16 bg-white dark:bg-gray-800 shadow-sm flex items-center justify-between px-6 flex-shrink-0">
                <h2 id="page-title" class="text-xl font-semibold">Dashboard</h2>
                <div class="flex items-center space-x-4">
                    <button id="theme-toggle-btn" class="text-gray-500 dark:text-gray-400 hover:text-primary-500">
                        <i class="fas fa-sun"></i>
                    </button>
                    <div class="relative">
                        <i class="fas fa-bell text-xl text-gray-500 dark:text-gray-400"></i>
                        <span class="absolute -top-1 -right-1 bg-red-500 text-white text-xs w-4 h-4 rounded-full flex items-center justify-center">3</span>
                    </div>
                    <div class="flex items-center space-x-2">
                        <img src="https://placehold.co/40x40/10b981/ffffff?text=A" class="w-8 h-8 rounded-full" alt="Admin Avatar">
                        <span class="font-semibold text-sm">Admin</span>
                    </div>
                </div>
            </header>

            <!-- Page Content Area -->
            <div class="flex-1 overflow-y-auto p-6">
                
                <!-- DASHBOARD PAGE -->
                <div id="page-dashboard" class="admin-page active">
                    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
                        <div class="bg-white dark:bg-gray-800 p-5 rounded-lg shadow">
                            <div class="flex items-center justify-between">
                                <div>
                                    <p class="text-sm text-gray-500 dark:text-gray-400">Total Pengguna</p>
                                    <p class="text-3xl font-bold">1,257</p>
                                </div>
                                <div class="bg-primary-100 dark:bg-primary-900/50 p-3 rounded-full">
                                    <i class="fas fa-users text-2xl text-primary-500"></i>
                                </div>
                            </div>
                        </div>
                        <div class="bg-white dark:bg-gray-800 p-5 rounded-lg shadow">
                            <div class="flex items-center justify-between">
                                <div>
                                    <p class="text-sm text-gray-500 dark:text-gray-400">Member Premium</p>
                                    <p class="text-3xl font-bold">312</p>
                                </div>
                                <div class="bg-yellow-100 dark:bg-yellow-900/50 p-3 rounded-full">
                                    <i class="fas fa-star text-2xl text-yellow-500"></i>
                                </div>
                            </div>
                        </div>
                        <div class="bg-white dark:bg-gray-800 p-5 rounded-lg shadow">
                            <div class="flex items-center justify-between">
                                <div>
                                    <p class="text-sm text-gray-500 dark:text-gray-400">Sinyal Aktif</p>
                                    <p class="text-3xl font-bold">8</p>
                                </div>
                                <div class="bg-red-100 dark:bg-red-900/50 p-3 rounded-full">
                                    <i class="fas fa-broadcast-tower text-2xl text-red-500"></i>
                                </div>
                            </div>
                        </div>
                        <div class="bg-white dark:bg-gray-800 p-5 rounded-lg shadow">
                            <div class="flex items-center justify-between">
                                <div>
                                    <p class="text-sm text-gray-500 dark:text-gray-400">Pendapatan Bulan Ini</p>
                                    <p class="text-3xl font-bold">Rp 15jt</p>
                                </div>
                                <div class="bg-blue-100 dark:bg-blue-900/50 p-3 rounded-full">
                                    <i class="fas fa-wallet text-2xl text-blue-500"></i>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="mt-8 bg-white dark:bg-gray-800 p-5 rounded-lg shadow">
                        <h3 class="font-semibold mb-4">Konten Terpopuler</h3>
                        <ul class="space-y-3">
                            <li class="flex justify-between items-center"><span>Artikel: Dasar-dasar Candlestick</span> <span class="text-gray-500">1.2k views</span></li>
                            <li class="flex justify-between items-center"><span>Video: Manajemen Risiko</span> <span class="text-gray-500">980 views</span></li>
                            <li class="flex justify-between items-center"><span>E-Book: Psikologi Trading</span> <span class="text-gray-500">750 downloads</span></li>
                        </ul>
                    </div>
                </div>

                <!-- USERS PAGE -->
                <div id="page-users" class="admin-page">
                    <div class="bg-white dark:bg-gray-800 p-5 rounded-lg shadow">
                        <div class="flex justify-between items-center mb-4">
                            <h3 class="font-semibold">Daftar Pengguna</h3>
                            <input type="text" placeholder="Cari pengguna..." class="px-3 py-1.5 bg-gray-50 dark:bg-gray-700 border rounded-md focus:outline-none focus:ring-2 focus:ring-primary-500">
                        </div>
                        <table class="w-full text-sm text-left">
                            <thead class="bg-gray-50 dark:bg-gray-700 text-gray-600 dark:text-gray-300 uppercase">
                                <tr>
                                    <th class="p-3">Nama</th>
                                    <th class="p-3">Email</th>
                                    <th class="p-3">Status</th>
                                    <th class="p-3">Tanggal Bergabung</th>
                                    <th class="p-3">Aksi</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr class="border-b dark:border-gray-700">
                                    <td class="p-3 font-medium">Andi Wijaya</td>
                                    <td class="p-3">andi.wijaya@email.com</td>
                                    <td class="p-3"><span class="px-2 py-1 text-xs font-semibold rounded-full bg-green-100 text-green-800 dark:bg-green-900 dark:text-green-300">Premium</span></td>
                                    <td class="p-3">2024-01-15</td>
                                    <td class="p-3 space-x-2"><button class="text-blue-500"><i class="fas fa-edit"></i></button><button class="text-red-500"><i class="fas fa-ban"></i></button></td>
                                </tr>
                                <tr class="border-b dark:border-gray-700">
                                    <td class="p-3 font-medium">Budi Santoso</td>
                                    <td class="p-3">budi.s@email.com</td>
                                    <td class="p-3"><span class="px-2 py-1 text-xs font-semibold rounded-full bg-gray-200 text-gray-800 dark:bg-gray-600 dark:text-gray-200">Free</span></td>
                                    <td class="p-3">2024-03-01</td>
                                    <td class="p-3 space-x-2"><button class="text-blue-500"><i class="fas fa-edit"></i></button><button class="text-red-500"><i class="fas fa-ban"></i></button></td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>

                <!-- SIGNALS PAGE -->
                <div id="page-signals" class="admin-page">
                    <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
                        <div class="lg:col-span-1 bg-white dark:bg-gray-800 p-5 rounded-lg shadow">
                            <h3 class="font-semibold mb-4">Buat Sinyal Baru</h3>
                            <form class="space-y-4">
                                <div>
                                    <label class="text-sm font-medium">Pair</label>
                                    <input type="text" placeholder="e.g., BTC/USDT" class="mt-1 w-full px-3 py-2 bg-gray-50 dark:bg-gray-700 border rounded-md focus:outline-none focus:ring-2 focus:ring-primary-500">
                                </div>
                                <div>
                                    <label class="text-sm font-medium">Rekomendasi</label>
                                    <select class="mt-1 w-full px-3 py-2 bg-gray-50 dark:bg-gray-700 border rounded-md focus:outline-none focus:ring-2 focus:ring-primary-500">
                                        <option>BUY</option>
                                        <option>SELL</option>
                                    </select>
                                </div>
                                <div>
                                    <label class="text-sm font-medium">Stop Loss (SL)</label>
                                    <input type="number" class="mt-1 w-full px-3 py-2 bg-gray-50 dark:bg-gray-700 border rounded-md focus:outline-none focus:ring-2 focus:ring-primary-500">
                                </div>
                                <div>
                                    <label class="text-sm font-medium">Take Profit (TP)</label>
                                    <div class="mt-1 space-y-2">
                                        <input type="number" placeholder="TP 1" class="w-full px-3 py-2 bg-gray-50 dark:bg-gray-700 border rounded-md focus:outline-none focus:ring-2 focus:ring-primary-500">
                                        <input type="number" placeholder="TP 2 (Opsional)" class="w-full px-3 py-2 bg-gray-50 dark:bg-gray-700 border rounded-md focus:outline-none focus:ring-2 focus:ring-primary-500">
                                        <input type="number" placeholder="TP 3 (Opsional)" class="w-full px-3 py-2 bg-gray-50 dark:bg-gray-700 border rounded-md focus:outline-none focus:ring-2 focus:ring-primary-500">
                                    </div>
                                </div>
                                <div class="flex items-center">
                                    <input type="checkbox" id="isPremiumSignal" class="h-4 w-4 text-primary-600 focus:ring-primary-500 border-gray-300 rounded">
                                    <label for="isPremiumSignal" class="ml-2 block text-sm">Sinyal Premium</label>
                                </div>
                                <button type="submit" class="w-full bg-primary-600 text-white py-2 rounded-lg hover:bg-primary-700 font-semibold">Kirim Sinyal</button>
                            </form>
                        </div>
                        <div class="lg:col-span-2 bg-white dark:bg-gray-800 p-5 rounded-lg shadow">
                            <h3 class="font-semibold mb-4">Daftar Sinyal Terkirim</h3>
                             <p class="text-gray-500">Daftar sinyal akan ditampilkan di sini.</p>
                        </div>
                    </div>
                </div>
                
                <!-- CONTENT PAGE -->
                <div id="page-content" class="admin-page">
                    <p class="text-gray-500">Halaman untuk mengelola Artikel, Video, dan E-Book.</p>
                </div>

                <!-- EVENTS PAGE -->
                <div id="page-events" class="admin-page">
                     <p class="text-gray-500">Halaman untuk mengelola event online dan offline.</p>
                </div>

                <!-- PAYMENTS PAGE -->
                <div id="page-payments" class="admin-page">
                    <div class="bg-white dark:bg-gray-800 p-5 rounded-lg shadow">
                        <h3 class="font-semibold mb-4">Konfirmasi Pembayaran Manual</h3>
                        <table class="w-full text-sm text-left">
                             <thead class="bg-gray-50 dark:bg-gray-700 text-gray-600 dark:text-gray-300 uppercase">
                                <tr>
                                    <th class="p-3">User ID</th>
                                    <th class="p-3">Email</th>
                                    <th class="p-3">Waktu Request</th>
                                    <th class="p-3">Aksi</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr class="border-b dark:border-gray-700">
                                    <td class="p-3 font-mono">user-xyz-123</td>
                                    <td class="p-3">siti.a@email.com</td>
                                    <td class="p-3">2024-05-20 10:30</td>
                                    <td class="p-3"><button class="bg-green-500 text-white px-3 py-1 rounded-md text-xs hover:bg-green-600">Konfirmasi</button></td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>

                <!-- SETTINGS PAGE -->
                <div id="page-settings" class="admin-page space-y-6">
                    <div class="bg-white dark:bg-gray-800 p-5 rounded-lg shadow">
                         <h3 class="font-semibold mb-4">Pengaturan Tampilan Beranda</h3>
                         <p class="text-sm text-gray-500 mb-4">Seret dan lepas untuk mengatur urutan konten di beranda aplikasi.</p>
                         <ul class="space-y-2" id="home-layout-list">
                             <li class="p-3 bg-gray-100 dark:bg-gray-700 rounded-md flex items-center justify-between cursor-move"><span class="flex items-center"><i class="fas fa-grip-vertical mr-3 text-gray-400"></i> Banner Promosi</span><button class="text-gray-400 hover:text-red-500"><i class="fas fa-times-circle"></i></button></li>
                             <li class="p-3 bg-gray-100 dark:bg-gray-700 rounded-md flex items-center justify-between cursor-move"><span class="flex items-center"><i class="fas fa-grip-vertical mr-3 text-gray-400"></i> Sinyal Premium</span><button class="text-gray-400 hover:text-red-500"><i class="fas fa-times-circle"></i></button></li>
                             <li class="p-3 bg-gray-100 dark:bg-gray-700 rounded-md flex items-center justify-between cursor-move"><span class="flex items-center"><i class="fas fa-grip-vertical mr-3 text-gray-400"></i> Artikel Edukasi</span><button class="text-gray-400 hover:text-red-500"><i class="fas fa-times-circle"></i></button></li>
                             <li class="p-3 bg-gray-100 dark:bg-gray-700 rounded-md flex items-center justify-between cursor-move"><span class="flex items-center"><i class="fas fa-grip-vertical mr-3 text-gray-400"></i> Postingan Komunitas</span><button class="text-gray-400 hover:text-red-500"><i class="fas fa-times-circle"></i></button></li>
                         </ul>
                         <button class="mt-4 w-full border-2 border-dashed border-gray-300 dark:border-gray-600 text-gray-500 dark:text-gray-400 py-2 rounded-lg hover:bg-gray-50 dark:hover:bg-gray-700/50 flex items-center justify-center">
                            <i class="fas fa-plus mr-2"></i> Tambah Konten
                         </button>
                    </div>
                    <div class="bg-white dark:bg-gray-800 p-5 rounded-lg shadow">
                        <h3 class="font-semibold mb-4">Pengaturan Aplikasi</h3>
                        <div class="space-y-4">
                            <div>
                                <label class="text-sm font-medium">Nama Aplikasi</label>
                                <input type="text" value="SignalMax" class="mt-1 w-full px-3 py-2 bg-gray-50 dark:bg-gray-700 border rounded-md focus:outline-none focus:ring-2 focus:ring-primary-500">
                            </div>
                            <div>
                                <label class="text-sm font-medium">Logo Aplikasi</label>
                                <div class="mt-1 flex items-center space-x-4">
                                    <img src="https://placehold.co/64x64/22c55e/ffffff?text=S" class="w-16 h-16 rounded-lg bg-gray-200" alt="Current Logo">
                                    <input type="file" class="text-sm text-gray-500 file:mr-4 file:py-2 file:px-4 file:rounded-full file:border-0 file:text-sm file:font-semibold file:bg-primary-50 file:text-primary-700 hover:file:bg-primary-100">
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="bg-white dark:bg-gray-800 p-5 rounded-lg shadow">
                        <h3 class="font-semibold mb-4">Pengaturan Iklan (AdMob)</h3>
                        <div class="space-y-4">
                            <div>
                                <label class="text-sm font-medium">ID Unit Iklan Banner</label>
                                <input type="text" placeholder="ca-app-pub-xxxxxxxxxxxxxxxx/xxxxxxxxxx" class="mt-1 w-full px-3 py-2 bg-gray-50 dark:bg-gray-700 border rounded-md focus:outline-none focus:ring-2 focus:ring-primary-500 font-mono text-xs">
                            </div>
                            <div>
                                <label class="text-sm font-medium">ID Unit Iklan Interstitial</label>
                                <input type="text" placeholder="ca-app-pub-xxxxxxxxxxxxxxxx/xxxxxxxxxx" class="mt-1 w-full px-3 py-2 bg-gray-50 dark:bg-gray-700 border rounded-md focus:outline-none focus:ring-2 focus:ring-primary-500 font-mono text-xs">
                            </div>
                            <div>
                                <label class="text-sm font-medium">ID Unit Iklan Rewarded</label>
                                <input type="text" placeholder="ca-app-pub-xxxxxxxxxxxxxxxx/xxxxxxxxxx" class="mt-1 w-full px-3 py-2 bg-gray-50 dark:bg-gray-700 border rounded-md focus:outline-none focus:ring-2 focus:ring-primary-500 font-mono text-xs">
                            </div>
                        </div>
                    </div>
                     <div class="pt-2 text-right">
                        <button class="bg-primary-600 text-white py-2 px-6 rounded-lg hover:bg-primary-700 font-semibold">Simpan Semua Pengaturan</button>
                    </div>
                </div>

            </div>
        </main>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const sidebarLinks = document.querySelectorAll('.sidebar-link');
            const adminPages = document.querySelectorAll('.admin-page');
            const pageTitle = document.getElementById('page-title');
            const themeToggleBtn = document.getElementById('theme-toggle-btn');
            const html = document.documentElement;

            // Page switching logic
            sidebarLinks.forEach(link => {
                link.addEventListener('click', (e) => {
                    e.preventDefault();
                    
                    const targetId = link.dataset.target;
                    
                    // Update active link
                    sidebarLinks.forEach(l => l.classList.remove('active'));
                    link.classList.add('active');

                    // Show target page
                    adminPages.forEach(page => {
                        page.classList.remove('active');
                    });
                    document.getElementById(targetId).classList.add('active');

                    // Update page title
                    pageTitle.textContent = link.querySelector('span').textContent;
                });
            });

            // Theme toggle logic
            const sunIcon = '<i class="fas fa-sun"></i>';
            const moonIcon = '<i class="fas fa-moon"></i>';

            const updateThemeIcon = () => {
                if (html.classList.contains('dark')) {
                    themeToggleBtn.innerHTML = sunIcon;
                } else {
                    themeToggleBtn.innerHTML = moonIcon;
                }
            };
            
            themeToggleBtn.addEventListener('click', () => {
                html.classList.toggle('dark');
                updateThemeIcon();
            });

            // Set initial theme icon
            updateThemeIcon();
        });
    </script>

</body>
</html>
            background: transparent;
        }
        .custom-scrollbar::-webkit-scrollbar-thumb {
            background: #888;
            border-radius: 2px;
        }
        .dark .custom-scrollbar::-webkit-scrollbar-thumb {
            background: #555;
        }
        .page {
            display: none;
        }
        .page.active {
            display: block;
        }
        /* Active nav item style */
        .nav-item.active i, .nav-item.active span {
            color: #22c55e; /* green-500 */
        }
        .dark .nav-item.active i, .dark .nav-item.active span {
            color: #4ade80; /* green-400 */
        }
    </style>
</head>
<body class="bg-gray-200 dark:bg-gray-900 flex items-center justify-center min-h-screen">

    <!-- Mobile Phone Frame -->
    <div class="w-full max-w-sm h-[800px] max-h-[90vh] bg-white dark:bg-black rounded-[40px] shadow-2xl border-8 border-gray-800 dark:border-gray-600 overflow-hidden flex flex-col">

        <!-- Main Screen Content -->
        <main id="main-content" class="flex-1 overflow-y-auto custom-scrollbar">

            <!-- ======================================= -->
            <!--            LOGIN SCREEN                 -->
            <!-- ======================================= -->
            <div id="screen-login" class="page active p-6 h-full flex flex-col justify-center bg-gray-50 dark:bg-gray-900">
                <div class="text-center mb-10">
                    <i class="fas fa-chart-line text-5xl text-green-500"></i>
                    <h1 class="text-4xl font-bold text-gray-800 dark:text-white mt-4">SignalMax</h1>
                    <p class="text-gray-500 dark:text-gray-400">Your Trading Signal Partner</p>
                </div>

                <div class="space-y-4">
                    <div>
                        <label for="email" class="text-sm font-medium text-gray-700 dark:text-gray-300">Email</label>
                        <input type="email" id="email" class="mt-1 block w-full px-3 py-2 bg-white dark:bg-gray-800 border border-gray-300 dark:border-gray-600 rounded-md shadow-sm placeholder-gray-400 focus:outline-none focus:ring-green-500 focus:border-green-500">
                    </div>
                    <div>
                        <label for="password" class="text-sm font-medium text-gray-700 dark:text-gray-300">Password</label>
                        <input type="password" id="password" class="mt-1 block w-full px-3 py-2 bg-white dark:bg-gray-800 border border-gray-300 dark:border-gray-600 rounded-md shadow-sm placeholder-gray-400 focus:outline-none focus:ring-green-500 focus:border-green-500">
                    </div>
                </div>

                <div class="mt-6">
                    <button id="login-button" class="w-full flex justify-center py-3 px-4 border border-transparent rounded-md shadow-sm text-sm font-medium text-white bg-green-600 hover:bg-green-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-green-500">
                        Login
                    </button>
                </div>

                <div class="mt-4 text-center">
                    <a href="#" class="text-sm text-green-600 hover:text-green-500">Lupa Password?</a>
                </div>

                <div class="mt-6 relative">
                    <div class="absolute inset-0 flex items-center">
                        <div class="w-full border-t border-gray-300 dark:border-gray-600"></div>
                    </div>
                    <div class="relative flex justify-center text-sm">
                        <span class="px-2 bg-gray-50 dark:bg-gray-900 text-gray-500 dark:text-gray-400">Atau lanjut dengan</span>
                    </div>
                </div>

                <div class="mt-6">
                     <button class="w-full flex items-center justify-center py-2 px-4 border border-gray-300 dark:border-gray-600 rounded-md shadow-sm text-sm font-medium text-gray-700 dark:text-white bg-white dark:bg-gray-800 hover:bg-gray-50 dark:hover:bg-gray-700">
                        <i class="fab fa-google text-red-500 mr-2"></i>
                        Login dengan Google
                    </button>
                </div>
                 <div class="mt-8 text-center">
                    <p class="text-sm text-gray-600 dark:text-gray-400">
                        Belum punya akun? <a href="#" class="font-medium text-green-600 hover:text-green-500">Daftar</a>
                    </p>
                </div>
            </div>

            <!-- ======================================= -->
            <!--             HOME SCREEN                 -->
            <!-- ======================================= -->
            <div id="screen-home" class="page p-4 space-y-6 bg-gray-50 dark:bg-gray-900">
                <!-- Header -->
                <div class="flex justify-between items-center">
                    <div>
                        <h1 class="text-2xl font-bold text-gray-800 dark:text-white">Beranda</h1>
                        <p class="text-sm text-gray-500 dark:text-gray-400">Selamat Datang, Andi!</p>
                    </div>
                    <div class="flex items-center space-x-4">
                        <button id="theme-toggle" class="text-gray-600 dark:text-gray-300">
                            <i class="fas fa-sun"></i>
                        </button>
                        <i class="fas fa-bell text-xl text-gray-600 dark:text-gray-300"></i>
                    </div>
                </div>

                <!-- Banner -->
                <div class="bg-green-500 text-white p-4 rounded-lg shadow-lg">
                    <h2 class="font-bold text-lg">Menjadi Anggota Premium</h2>
                    <p class="text-sm mt-1">Dapatkan akses sinyal eksklusif dan materi edukasi lengkap.</p>
                    <button class="bg-white text-green-600 font-bold py-1 px-3 rounded-full mt-3 text-sm">Upgrade Sekarang</button>
                </div>

                <!-- Premium Signals -->
                <div>
                    <h3 class="font-semibold text-lg text-gray-700 dark:text-gray-200 mb-2">Sinyal Premium Terbaru</h3>
                    <div class="space-y-3">
                        <div class="bg-white dark:bg-gray-800 p-3 rounded-lg shadow flex items-center justify-between">
                            <div class="flex items-center">
                                <div class="bg-green-100 dark:bg-green-900 p-2 rounded-full mr-3">
                                    <i class="fas fa-arrow-up text-green-500"></i>
                                </div>
                                <div>
                                    <p class="font-bold text-gray-800 dark:text-white">BTC/USDT</p>
                                    <p class="text-sm text-green-500 font-semibold">BUY</p>
                                </div>
                            </div>
                            <div class="text-right">
                                 <p class="font-semibold text-gray-800 dark:text-white">$68,500.50</p>
                                 <p class="text-xs text-gray-500 dark:text-gray-400">5 menit lalu</p>
                            </div>
                        </div>
                         <div class="bg-white dark:bg-gray-800 p-3 rounded-lg shadow flex items-center justify-between">
                            <div class="flex items-center">
                                <div class="bg-red-100 dark:bg-red-900 p-2 rounded-full mr-3">
                                    <i class="fas fa-arrow-down text-red-500"></i>
                                </div>
                                <div>
                                    <p class="font-bold text-gray-800 dark:text-white">ETH/USDT</p>
                                    <p class="text-sm text-red-500 font-semibold">SELL</p>
                                </div>
                            </div>
                            <div class="text-right">
                                 <p class="font-semibold text-gray-800 dark:text-white">$3,420.10</p>
                                 <p class="text-xs text-gray-500 dark:text-gray-400">30 menit lalu</p>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Education Articles -->
                <div>
                    <h3 class="font-semibold text-lg text-gray-700 dark:text-gray-200 mb-2">Edukasi Terkini</h3>
                    <div class="grid grid-cols-2 gap-4">
                        <div class="bg-white dark:bg-gray-800 rounded-lg shadow overflow-hidden">
                            <img src="https://placehold.co/400x200/a7f3d0/1f2937?text=Edukasi" alt="Edukasi" class="w-full h-20 object-cover">
                            <div class="p-3">
                                <p class="font-semibold text-sm text-gray-800 dark:text-white">Dasar-dasar Candlestick</p>
                            </div>
                        </div>
                        <div class="bg-white dark:bg-gray-800 rounded-lg shadow overflow-hidden">
                            <img src="https://placehold.co/400x200/fecaca/1f2937?text=Analisis" alt="Analisis" class="w-full h-20 object-cover">
                            <div class="p-3">
                                <p class="font-semibold text-sm text-gray-800 dark:text-white">Manajemen Risiko</p>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Community Post -->
                <div>
                    <h3 class="font-semibold text-lg text-gray-700 dark:text-gray-200 mb-2">Diskusi Komunitas</h3>
                    <div class="bg-white dark:bg-gray-800 p-3 rounded-lg shadow">
                        <div class="flex items-start space-x-3">
                            <img src="https://placehold.co/40x40/34d399/ffffff?text=B" alt="Avatar" class="w-10 h-10 rounded-full">
                            <div>
                                <p class="font-semibold text-gray-800 dark:text-white">Budi Santoso <span class="text-xs font-medium bg-green-100 text-green-800 dark:bg-green-900 dark:text-green-300 px-2 py-0.5 rounded-full">Premium</span></p>
                                <p class="text-sm text-gray-600 dark:text-gray-300 mt-1">Apakah ada yang punya pandangan tentang pergerakan SOL minggu ini? Sepertinya akan ada breakout.</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- ======================================= -->
            <!--           SIGNALS SCREEN                -->
            <!-- ======================================= -->
            <div id="screen-signals" class="page p-4 space-y-4 bg-gray-50 dark:bg-gray-900">
                <h1 class="text-2xl font-bold text-gray-800 dark:text-white">Sinyal Trading</h1>
                <!-- TradingView Placeholder -->
                <div class="bg-gray-200 dark:bg-gray-800 h-56 rounded-lg flex items-center justify-center">
                    <p class="text-gray-500">Embedded TradingView Chart</p>
                </div>
                <!-- Signal List -->
                <div class="space-y-3">
                    <div class="bg-white dark:bg-gray-800 p-4 rounded-lg shadow-md">
                        <div class="flex justify-between items-center mb-2">
                            <span class="font-bold text-lg text-gray-800 dark:text-white">BTC/USDT</span>
                            <span class="text-xs text-gray-500 dark:text-gray-400">1 jam lalu</span>
                        </div>
                        <div class="flex justify-between items-center bg-green-50 dark:bg-green-900/50 p-2 rounded-md">
                            <span class="font-semibold text-green-600 dark:text-green-400">REKOMENDASI: BUY</span>
                            <span class="font-bold text-lg text-gray-800 dark:text-white">$68,500</span>
                        </div>
                        <div class="mt-3 grid grid-cols-2 gap-2 text-sm">
                            <div class="bg-red-50 dark:bg-red-900/50 p-2 rounded">
                                <p class="text-red-600 dark:text-red-400 font-medium">Stop Loss</p>
                                <p class="font-semibold text-gray-700 dark:text-gray-200">$67,800</p>
                            </div>
                             <div class="bg-green-50 dark:bg-green-900/50 p-2 rounded">
                                <p class="text-green-600 dark:text-green-400 font-medium">Take Profit</p>
                                <p class="font-semibold text-gray-700 dark:text-gray-200">$70,000</p>
                            </div>
                        </div>
                         <div class="mt-2 text-right">
                             <span class="text-xs font-medium bg-green-100 text-green-800 dark:bg-green-900 dark:text-green-300 px-2 py-0.5 rounded-full">Premium</span>
                         </div>
                    </div>
                    <div class="bg-white dark:bg-gray-800 p-4 rounded-lg shadow-md opacity-50">
                        <div class="flex justify-between items-center mb-2">
                            <span class="font-bold text-lg text-gray-800 dark:text-white">ADA/USDT</span>
                            <span class="text-xs text-gray-500 dark:text-gray-400">3 jam lalu</span>
                        </div>
                        <div class="flex justify-center items-center h-20">
                            <i class="fas fa-lock text-gray-400 dark:text-gray-500 mr-2"></i>
                            <span class="text-gray-500 font-semibold">Upgrade ke Premium untuk melihat</span>
                        </div>
                    </div>
                </div>
            </div>

            <!-- ======================================= -->
            <!--          COMMUNITY SCREEN               -->
            <!-- ======================================= -->
            <div id="screen-community" class="page p-4 space-y-4 bg-gray-50 dark:bg-gray-900">
                <h1 class="text-2xl font-bold text-gray-800 dark:text-white">Komunitas</h1>
                <!-- Post creation -->
                <div class="bg-white dark:bg-gray-800 p-3 rounded-lg shadow">
                    <textarea class="w-full bg-transparent text-gray-700 dark:text-gray-300 focus:outline-none" rows="2" placeholder="Apa yang Anda pikirkan?"></textarea>
                    <div class="flex justify-between items-center mt-2">
                        <div>
                            <i class="fas fa-image text-green-500 cursor-pointer mr-2"></i>
                            <i class="fas fa-poll text-green-500 cursor-pointer"></i>
                        </div>
                        <button class="bg-green-500 text-white font-bold py-1 px-4 rounded-full text-sm">Posting</button>
                    </div>
                </div>
                <!-- Post feed -->
                <div class="space-y-4">
                    <div class="bg-white dark:bg-gray-800 p-3 rounded-lg shadow">
                        <div class="flex items-start space-x-3">
                            <img src="https://placehold.co/40x40/34d399/ffffff?text=B" alt="Avatar" class="w-10 h-10 rounded-full">
                            <div>
                                <p class="font-semibold text-gray-800 dark:text-white">Budi Santoso <span class="text-xs font-medium bg-green-100 text-green-800 dark:bg-green-900 dark:text-green-300 px-2 py-0.5 rounded-full">Premium</span></p>
                                <p class="text-xs text-gray-500 dark:text-gray-400">10 menit lalu</p>
                                <p class="text-sm text-gray-600 dark:text-gray-300 mt-2">Apakah ada yang punya pandangan tentang pergerakan SOL minggu ini? Sepertinya akan ada breakout.</p>
                                <div class="flex space-x-4 mt-3 text-gray-500 dark:text-gray-400">
                                    <span class="flex items-center"><i class="far fa-heart mr-1"></i> 15</span>
                                    <span class="flex items-center"><i class="far fa-comment mr-1"></i> 4</span>
                                </div>
                            </div>
                        </div>
                    </div>
                     <div class="bg-white dark:bg-gray-800 p-3 rounded-lg shadow">
                        <div class="flex items-start space-x-3">
                            <img src="https://placehold.co/40x40/f87171/ffffff?text=S" alt="Avatar" class="w-10 h-10 rounded-full">
                            <div>
                                <p class="font-semibold text-gray-800 dark:text-white">Siti Aminah</p>
                                <p class="text-xs text-gray-500 dark:text-gray-400">1 jam lalu</p>
                                <p class="text-sm text-gray-600 dark:text-gray-300 mt-2">Baru belajar trading, ada rekomendasi buku atau video untuk pemula?</p>
                                <div class="flex space-x-4 mt-3 text-gray-500 dark:text-gray-400">
                                    <span class="flex items-center"><i class="far fa-heart mr-1"></i> 8</span>
                                    <span class="flex items-center"><i class="far fa-comment mr-1"></i> 12</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- ======================================= -->
            <!--          EDUCATION SCREEN               -->
            <!-- ======================================= -->
            <div id="screen-education" class="page p-4 space-y-4 bg-gray-50 dark:bg-gray-900">
                <h1 class="text-2xl font-bold text-gray-800 dark:text-white">Pusat Edukasi</h1>
                <!-- Filters -->
                <div class="flex space-x-2">
                    <button class="bg-green-500 text-white px-3 py-1 text-sm rounded-full">Semua</button>
                    <button class="bg-gray-200 dark:bg-gray-700 text-gray-700 dark:text-gray-200 px-3 py-1 text-sm rounded-full">Pemula</button>
                    <button class="bg-gray-200 dark:bg-gray-700 text-gray-700 dark:text-gray-200 px-3 py-1 text-sm rounded-full">Menengah</button>
                </div>
                <!-- Content List -->
                <div class="space-y-3">
                    <div class="bg-white dark:bg-gray-800 p-3 rounded-lg shadow flex items-center space-x-4">
                        <i class="fas fa-file-alt text-2xl text-green-500 w-8 text-center"></i>
                        <div>
                            <p class="font-semibold text-gray-800 dark:text-white">Mengenal Support & Resistance</p>
                            <p class="text-sm text-gray-500 dark:text-gray-400">Artikel • Pemula</p>
                        </div>
                    </div>
                    <div class="bg-white dark:bg-gray-800 p-3 rounded-lg shadow flex items-center space-x-4">
                        <i class="fas fa-video text-2xl text-red-500 w-8 text-center"></i>
                        <div>
                            <p class="font-semibold text-gray-800 dark:text-white">Video: Analisis Teknikal Lanjutan</p>
                            <p class="text-sm text-gray-500 dark:text-gray-400">Video • Menengah</p>
                        </div>
                    </div>
                    <div class="bg-white dark:bg-gray-800 p-3 rounded-lg shadow flex items-center space-x-4 relative overflow-hidden">
                        <div class="absolute inset-0 bg-gray-200/50 dark:bg-gray-800/50 backdrop-blur-sm flex items-center justify-center">
                             <i class="fas fa-lock text-gray-400 dark:text-gray-500 mr-2"></i>
                            <span class="text-gray-500 font-semibold">Konten Premium</span>
                        </div>
                         <i class="fas fa-book text-2xl text-green-500 w-8 text-center"></i>
                        <div>
                            <p class="font-semibold text-gray-800 dark:text-white">E-Book: Psikologi Trading</p>
                            <p class="text-sm text-gray-500 dark:text-gray-400">E-Book • Profesional</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- ======================================= -->
            <!--            PROFILE SCREEN               -->
            <!-- ======================================= -->
            <div id="screen-profile" class="page bg-gray-50 dark:bg-gray-900">
                <div class="p-4 bg-white dark:bg-gray-800 shadow-md">
                    <div class="flex items-center space-x-4">
                        <img src="https://placehold.co/80x80/10b981/ffffff?text=A" alt="Profile" class="w-20 h-20 rounded-full border-4 border-green-400">
                        <div>
                            <h2 class="text-xl font-bold text-gray-800 dark:text-white">Andi Wijaya</h2>
                            <p class="text-gray-500 dark:text-gray-400">andi.wijaya@email.com</p>
                            <span class="mt-1 inline-block text-xs font-medium bg-green-100 text-green-800 dark:bg-green-900 dark:text-green-300 px-2.5 py-1 rounded-full">
                                <i class="fas fa-star mr-1"></i>Premium Member
                            </span>
                        </div>
                    </div>
                </div>
                <div class="p-4 mt-4 space-y-2">
                    <a href="#" class="flex items-center justify-between p-3 bg-white dark:bg-gray-800 rounded-lg shadow-sm">
                        <span class="text-gray-700 dark:text-gray-200"><i class="fas fa-user-edit w-6 mr-2 text-green-500"></i>Edit Profil</span>
                        <i class="fas fa-chevron-right text-gray-400"></i>
                    </a>
                    <a href="#" class="flex items-center justify-between p-3 bg-white dark:bg-gray-800 rounded-lg shadow-sm">
                        <span class="text-gray-700 dark:text-gray-200"><i class="fas fa-bell w-6 mr-2 text-green-500"></i>Pengaturan Notifikasi</span>
                        <i class="fas fa-chevron-right text-gray-400"></i>
                    </a>
                     <a href="#" class="flex items-center justify-between p-3 bg-white dark:bg-gray-800 rounded-lg shadow-sm">
                        <span class="text-gray-700 dark:text-gray-200"><i class="fas fa-calendar-alt w-6 mr-2 text-green-500"></i>Event Saya</span>
                        <i class="fas fa-chevron-right text-gray-400"></i>
                    </a>
                    <a href="#" class="flex items-center justify-between p-3 bg-white dark:bg-gray-800 rounded-lg shadow-sm">
                        <span class="text-gray-700 dark:text-gray-200"><i class="fas fa-shield-alt w-6 mr-2 text-green-500"></i>Keamanan</span>
                        <i class="fas fa-chevron-right text-gray-400"></i>
                    </a>
                    <div class="pt-4">
                         <a href="#" id="logout-button" class="flex items-center justify-between p-3 bg-white dark:bg-gray-800 rounded-lg shadow-sm">
                            <span class="text-red-500 font-semibold"><i class="fas fa-sign-out-alt w-6 mr-2"></i>Keluar</span>
                        </a>
                    </div>
                </div>
            </div>

        </main>

        <!-- Bottom Navigation Bar -->
        <nav class="bg-white dark:bg-gray-800 border-t border-gray-200 dark:border-gray-700 flex justify-around">
            <button data-target="screen-home" class="nav-item flex-1 flex flex-col items-center justify-center py-2 text-gray-500 dark:text-gray-400 text-xs active">
                <i class="fas fa-home text-xl"></i>
                <span>Beranda</span>
            </button>
            <button data-target="screen-signals" class="nav-item flex-1 flex flex-col items-center justify-center py-2 text-gray-500 dark:text-gray-400 text-xs">
                <i class="fas fa-chart-line text-xl"></i>
                <span>Sinyal</span>
            </button>
            <button data-target="screen-community" class="nav-item flex-1 flex flex-col items-center justify-center py-2 text-gray-500 dark:text-gray-400 text-xs">
                <i class="fas fa-users text-xl"></i>
                <span>Komunitas</span>
            </button>
            <button data-target="screen-education" class="nav-item flex-1 flex flex-col items-center justify-center py-2 text-gray-500 dark:text-gray-400 text-xs">
                <i class="fas fa-book-open text-xl"></i>
                <span>Edukasi</span>
            </button>
            <button data-target="screen-profile" class="nav-item flex-1 flex flex-col items-center justify-center py-2 text-gray-500 dark:text-gray-400 text-xs">
                <i class="fas fa-user-circle text-xl"></i>
                <span>Profil</span>
            </button>
        </nav>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const navItems = document.querySelectorAll('.nav-item');
            const pages = document.querySelectorAll('.page');
            const themeToggle = document.getElementById('theme-toggle');
            const loginButton = document.getElementById('login-button');
            const logoutButton = document.getElementById('logout-button');
            const html = document.documentElement;

            // Function to switch pages
            const showPage = (targetId) => {
                pages.forEach(page => {
                    page.classList.remove('active');
                });
                const targetPage = document.getElementById(targetId);
                if (targetPage) {
                    targetPage.classList.add('active');
                }
            };

            // Navigation logic
            navItems.forEach(item => {
                item.addEventListener('click', () => {
                    const targetId = item.dataset.target;
                    showPage(targetId);
                    
                    navItems.forEach(nav => nav.classList.remove('active'));
                    item.classList.add('active');
                });
            });
            
            // Initial page setup
            showPage('screen-login');
            document.querySelector('.nav-item[data-target="screen-home"]').classList.add('active');


            // Login/Logout simulation
            loginButton.addEventListener('click', () => {
                showPage('screen-home');
            });

            logoutButton.addEventListener('click', (e) => {
                e.preventDefault();
                showPage('screen-login');
                navItems.forEach(nav => nav.classList.remove('active'));
                document.querySelector('.nav-item[data-target="screen-home"]').classList.add('active');
            });


            // Theme toggle logic
            const sunIcon = '<i class="fas fa-sun"></i>';
            const moonIcon = '<i class="fas fa-moon"></i>';

            const updateThemeIcon = () => {
                if (html.classList.contains('dark')) {
                    themeToggle.innerHTML = sunIcon;
                } else {
                    themeToggle.innerHTML = moonIcon;
                }
            };

            themeToggle.addEventListener('click', () => {
                html.classList.toggle('dark');
                updateThemeIcon();
            });

            // Set initial theme icon
            updateThemeIcon();
        });
    </script>
</body>
</html>
