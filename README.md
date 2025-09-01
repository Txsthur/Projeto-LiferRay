<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Liferay Cares - Portal de Voluntariado</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f8fafc;
        }
        .page {
            display: none;
        }
        .page.active {
            display: block;
        }
        /* Custom scrollbar for better aesthetics */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #f1f1f1;
        }
        ::-webkit-scrollbar-thumb {
            background: #cbd5e1;
            border-radius: 10px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #94a3b8;
        }
    </style>
</head>
<body class="text-slate-800">

    <!-- Header -->
    <header class="bg-white shadow-md sticky top-0 z-50">
        <nav class="container mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-16">
                <div class="flex items-center">
                    <div class="flex-shrink-0">
                         <h1 class="text-2xl font-bold text-blue-600">Liferay Cares</h1>
                    </div>
                </div>
                <div class="hidden md:block">
                    <div class="ml-10 flex items-baseline space-x-4">
                        <a href="#oportunidades" class="nav-link text-gray-700 hover:bg-blue-500 hover:text-white px-3 py-2 rounded-md text-sm font-medium">Oportunidades</a>
                        <a href="#impacto" class="nav-link text-gray-700 hover:bg-blue-500 hover:text-white px-3 py-2 rounded-md text-sm font-medium">Painel de Impacto</a>
                        <a href="#perfil" class="nav-link text-gray-700 hover:bg-blue-500 hover:text-white px-3 py-2 rounded-md text-sm font-medium">Meu Perfil</a>
                    </div>
                </div>
                 <div class="md:hidden">
                    <button id="mobile-menu-button" class="inline-flex items-center justify-center p-2 rounded-md text-gray-400 hover:text-white hover:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-800 focus:ring-white">
                        <span class="sr-only">Open main menu</span>
                        <svg class="h-6 w-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" aria-hidden="true">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7" />
                        </svg>
                    </button>
                </div>
            </div>
        </nav>
        <div id="mobile-menu" class="md:hidden hidden">
            <div class="px-2 pt-2 pb-3 space-y-1 sm:px-3">
                <a href="#oportunidades" class="nav-link text-gray-700 hover:bg-blue-500 hover:text-white block px-3 py-2 rounded-md text-base font-medium">Oportunidades</a>
                <a href="#impacto" class="nav-link text-gray-700 hover:bg-blue-500 hover:text-white block px-3 py-2 rounded-md text-base font-medium">Painel de Impacto</a>
                <a href="#perfil" class="nav-link text-gray-700 hover:bg-blue-500 hover:text-white block px-3 py-2 rounded-md text-base font-medium">Meu Perfil</a>
            </div>
        </div>
    </header>

    <main class="container mx-auto p-4 sm:p-6 lg:p-8">

        <!-- Page: Oportunidades -->
        <div id="oportunidades" class="page active">
            <div class="bg-white p-6 rounded-lg shadow-lg mb-6">
                <h2 class="text-2xl font-bold mb-4">Encontre uma Causa</h2>
                <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                    <input id="search-input" type="text" placeholder="Pesquisar por nome, ONG..." class="md:col-span-2 w-full px-4 py-2 border border-slate-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500">
                    <select id="filter-local" class="w-full px-4 py-2 border border-slate-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500">
                        <option value="todos">Todos os Locais</option>
                        <option value="Online">Online</option>
                        <option value="Presencial">Presencial</option>
                    </select>
                </div>
                 <div class="flex justify-between items-center mt-4">
                    <button id="create-opportunity-btn" class="bg-green-500 text-white px-4 py-2 rounded-md hover:bg-green-600 transition-colors flex items-center gap-2">
                        <i data-lucide="plus-circle" class="w-5 h-5"></i> Criar Oportunidade
                    </button>
                    <div class="flex items-center space-x-2">
                        <label for="admin-toggle" class="text-sm font-medium text-gray-700">Modo Admin</label>
                        <input type="checkbox" id="admin-toggle" class="h-4 w-4 rounded border-gray-300 text-blue-600 focus:ring-blue-500">
                    </div>
                </div>
            </div>
            <div id="opportunities-list" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                <!-- Cards de Oportunidades serão inseridos aqui -->
            </div>
        </div>

        <!-- Page: Painel de Impacto -->
        <div id="impacto" class="page">
            <div class="bg-white p-8 rounded-lg shadow-lg text-center">
                <h2 class="text-3xl font-bold mb-6">Nosso Impacto Coletivo</h2>
                <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                    <div class="bg-blue-100 p-6 rounded-lg">
                        <h3 class="text-xl font-semibold text-blue-800">Horas de Voluntariado</h3>
                        <p id="total-hours" class="text-5xl font-bold text-blue-600 mt-2">0</p>
                    </div>
                    <div class="bg-green-100 p-6 rounded-lg">
                        <h3 class="text-xl font-semibold text-green-800">Oportunidades Concluídas</h3>
                        <p id="completed-opportunities" class="text-5xl font-bold text-green-600 mt-2">0</p>
                    </div>
                    <div class="bg-yellow-100 p-6 rounded-lg">
                        <h3 class="text-xl font-semibold text-yellow-800">Voluntários Ativos</h3>
                        <p id="active-volunteers" class="text-5xl font-bold text-yellow-600 mt-2">0</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Page: Meu Perfil -->
        <div id="perfil" class="page">
            <div class="bg-white p-8 rounded-lg shadow-lg">
                <div class="flex flex-col sm:flex-row items-center sm:items-start gap-6">
                    <img src="https://placehold.co/128x128/E0E7FF/4F46E5?text=AV" alt="Foto do Perfil" class="w-32 h-32 rounded-full border-4 border-blue-500">
                    <div>
                        <h2 id="user-name" class="text-3xl font-bold">Nome do Colaborador</h2>
                        <p class="text-slate-500">Engenheiro de Software</p>
                        <div class="mt-4 bg-blue-100 p-4 rounded-lg inline-block">
                            <p class="text-lg font-semibold text-blue-800">Total de Horas Contribuídas</p>
                            <p id="user-total-hours" class="text-4xl font-bold text-blue-600">0</p>
                        </div>
                    </div>
                </div>

                <div class="mt-10">
                    <h3 class="text-2xl font-bold mb-4">Minhas Inscrições</h3>
                    <div class="space-y-6">
                        <div>
                            <h4 class="text-xl font-semibold mb-2 text-slate-600">Próximas Oportunidades</h4>
                            <div id="upcoming-registrations" class="space-y-4">
                                <!-- Inscrições futuras aqui -->
                            </div>
                        </div>
                        <div>
                            <h4 class="text-xl font-semibold mb-2 text-slate-600">Histórico de Participação</h4>
                            <div id="past-registrations" class="space-y-4">
                               <!-- Histórico aqui -->
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </main>

    <!-- Modal: Detalhes da Oportunidade -->
    <div id="details-modal" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4 hidden z-50">
        <div class="bg-white rounded-lg shadow-2xl w-full max-w-2xl max-h-[90vh] overflow-y-auto">
            <div class="p-6" id="details-modal-content">
                <!-- Conteúdo do modal será inserido aqui -->
            </div>
            <div class="p-4 bg-slate-50 border-t flex justify-end gap-2">
                <button id="close-details-modal" class="px-4 py-2 bg-slate-200 text-slate-800 rounded-md hover:bg-slate-300">Fechar</button>
                <button id="register-btn" class="px-4 py-2 bg-blue-600 text-white rounded-md hover:bg-blue-700">Inscrever-se</button>
            </div>
        </div>
    </div>

    <!-- Modal: Criar Oportunidade -->
    <div id="create-modal" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4 hidden z-50">
        <div class="bg-white rounded-lg shadow-2xl w-full max-w-2xl max-h-[90vh] overflow-y-auto">
            <form id="create-opportunity-form" class="p-6 space-y-4">
                <h2 class="text-2xl font-bold">Criar Nova Oportunidade</h2>
                <input type="text" name="name" placeholder="Nome da Oportunidade" class="w-full p-2 border rounded" required>
                <textarea name="description" placeholder="Descrição completa" class="w-full p-2 border rounded" rows="4" required></textarea>
                <input type="text" name="ong" placeholder="Nome da ONG/Instituição" class="w-full p-2 border rounded" required>
                <select name="locationType" class="w-full p-2 border rounded" required>
                    <option value="Presencial">Presencial</option>
                    <option value="Online">Online</option>
                </select>
                <input type="text" name="cityCountry" placeholder="Cidade/País (para presencial)" class="w-full p-2 border rounded">
                <input type="datetime-local" name="date" class="w-full p-2 border rounded" required>
                <div class="p-4 bg-slate-50 border-t flex justify-end gap-2 mt-4 -mx-6 -mb-6">
                    <button type="button" id="close-create-modal" class="px-4 py-2 bg-slate-200 text-slate-800 rounded-md hover:bg-slate-300">Cancelar</button>
                    <button type="submit" class="px-4 py-2 bg-green-600 text-white rounded-md hover:bg-green-700">Enviar para Aprovação</button>
                </div>
            </form>
        </div>
    </div>

    <!-- Modal: Registrar Horas -->
    <div id="hours-modal" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4 hidden z-50">
        <div class="bg-white rounded-lg shadow-2xl w-full max-w-sm">
            <form id="hours-form" class="p-6 space-y-4">
                <h2 class="text-xl font-bold">Registrar Horas</h2>
                <p>Quantas horas você dedicou a <strong id="hours-opportunity-name"></strong>?</p>
                <input type="number" id="hours-input" min="1" class="w-full p-2 border rounded" required>
                <div class="flex justify-end gap-2">
                    <button type="button" id="close-hours-modal" class="px-4 py-2 bg-slate-200 rounded-md">Cancelar</button>
                    <button type="submit" class="px-4 py-2 bg-blue-600 text-white rounded-md">Salvar</button>
                </div>
            </form>
        </div>
    </div>
    
    <!-- Modal: Adicionar Testemunho -->
    <div id="testimonial-modal" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4 hidden z-50">
        <div class="bg-white rounded-lg shadow-2xl w-full max-w-lg">
            <form id="testimonial-form" class="p-6 space-y-4">
                <h2 class="text-xl font-bold">Compartilhe sua Experiência</h2>
                <p>Deixe um testemunho sobre <strong id="testimonial-opportunity-name"></strong>.</p>
                <textarea id="testimonial-text" class="w-full p-2 border rounded" rows="5" placeholder="Sua experiência foi incrível? Conte para nós..." required></textarea>
                <input type="text" id="testimonial-photo" class="w-full p-2 border rounded" placeholder="URL da foto (opcional, ex: https://...)">
                <div class="flex justify-end gap-2">
                    <button type="button" id="close-testimonial-modal" class="px-4 py-2 bg-slate-200 rounded-md">Cancelar</button>
                    <button type="submit" class="px-4 py-2 bg-blue-600 text-white rounded-md">Publicar</button>
                </div>
            </form>
        </div>
    </div>
    
    <!-- Custom Message Box -->
    <div id="message-box" class="fixed top-5 right-5 bg-green-500 text-white px-6 py-3 rounded-lg shadow-lg transform translate-x-[120%] transition-transform duration-300 z-50">
        <p id="message-text"></p>
    </div>


    <script>
        document.addEventListener('DOMContentLoaded', () => {
            // Inicializa os ícones do Lucide
            lucide.createIcons();

            // --- MOCK DATA (Simulando um banco de dados) ---
            let currentUser = {
                id: 1,
                name: 'Alex Silva',
                job: 'Engenheiro de Software',
                totalHours: 0,
            };

            let opportunities = [
                { id: 1, name: 'Mutirão de Limpeza na Praia', description: 'Vamos juntos limpar a praia de Boa Viagem, removendo lixo e conscientizando a população local sobre a importância da preservação ambiental.', ong: 'SOS Oceano', locationType: 'Presencial', cityCountry: 'Recife, Brasil', date: '2025-09-15T09:00:00', status: 'Aprovado' },
                { id: 2, name: 'Mentoria de Carreira para Jovens', description: 'Ofereça mentoria online para jovens de comunidades carentes que estão iniciando no mercado de trabalho. Compartilhe sua experiência!', ong: 'Futuro Brilhante', locationType: 'Online', cityCountry: '', date: '2025-10-05T18:00:00', status: 'Aprovado' },
                { id: 3, name: 'Doação de Sangue Coletiva', description: 'Uma campanha para incentivar a doação de sangue. Um pequeno gesto que salva muitas vidas. Participe no hemocentro mais próximo.', ong: 'Vida por Vidas', locationType: 'Presencial', cityCountry: 'São Paulo, Brasil', date: '2025-08-28T10:00:00', status: 'Aprovado' },
                { id: 4, name: 'Desenvolvimento de Site para ONG', description: 'Ajude a desenvolver o novo site da ONG "Criança Feliz", que atua com educação infantil. Vagas para desenvolvedores, designers e redatores.', ong: 'Criança Feliz', locationType: 'Online', cityCountry: '', date: '2025-09-20T14:00:00', status: 'Aprovado' },
                { id: 5, name: 'Arrecadação de Alimentos', description: 'Campanha de arrecadação de alimentos não perecíveis para distribuir a famílias em situação de vulnerabilidade social.', ong: 'Mesa Cheia', locationType: 'Presencial', cityCountry: 'Recife, Brasil', date: '2025-07-20T09:00:00', status: 'Concluído' },
                { id: 6, name: 'Revisão de Currículos', description: 'Ajude profissionais a melhorarem seus currículos para aumentar as chances de recolocação no mercado de trabalho.', ong: 'Emprega+', locationType: 'Online', cityCountry: '', date: '2025-06-10T19:00:00', status: 'Concluído' },
                { id: 7, name: 'Plantio de Árvores no Parque', description: 'Participe de uma manhã de plantio de mudas de árvores nativas para revitalizar uma área do Parque da Jaqueira.', ong: 'Verde Novo', locationType: 'Presencial', cityCountry: 'Recife, Brasil', date: '2025-11-02T08:30:00', status: 'Pendente' }
            ];

            let registrations = [
                { id: 1, userId: 1, opportunityId: 5, status: 'Concluído', hours: 4 },
                { id: 2, userId: 1, opportunityId: 6, status: 'Concluído', hours: 3 },
            ];
            
            let testimonials = [
                { id: 1, userId: 1, opportunityId: 5, text: 'Foi uma experiência incrível e muito organizada! Ver a comunidade unida por uma causa tão nobre foi emocionante.', photoUrl: 'https://placehold.co/600x400/a7f3d0/166534?text=Voluntariado' }
            ];

            let isAdminMode = false;

            // --- ELEMENTOS DO DOM ---
            const pages = document.querySelectorAll('.page');
            const navLinks = document.querySelectorAll('.nav-link');
            const opportunitiesList = document.getElementById('opportunities-list');
            const searchInput = document.getElementById('search-input');
            const filterLocal = document.getElementById('filter-local');
            
            // Modals
            const detailsModal = document.getElementById('details-modal');
            const createModal = document.getElementById('create-modal');
            const hoursModal = document.getElementById('hours-modal');
            const testimonialModal = document.getElementById('testimonial-modal');

            // --- FUNÇÕES DE RENDERIZAÇÃO ---
            
            function formatDate(dateString) {
                const options = { year: 'numeric', month: 'long', day: 'numeric', hour: '2-digit', minute: '2-digit' };
                return new Date(dateString).toLocaleDateString('pt-BR', options);
            }

            function renderOpportunities() {
                const searchTerm = searchInput.value.toLowerCase();
                const locationFilter = filterLocal.value;

                const filteredOpportunities = opportunities.filter(op => {
                    const matchesSearch = op.name.toLowerCase().includes(searchTerm) || op.ong.toLowerCase().includes(searchTerm) || op.description.toLowerCase().includes(searchTerm);
                    const matchesLocation = locationFilter === 'todos' || op.locationType === locationFilter;
                    const isVisible = isAdminMode ? true : op.status === 'Aprovado' || op.status === 'Concluído';
                    return matchesSearch && matchesLocation && isVisible;
                });

                opportunitiesList.innerHTML = '';
                if (filteredOpportunities.length === 0) {
                    opportunitiesList.innerHTML = `<p class="text-slate-500 col-span-full text-center">Nenhuma oportunidade encontrada.</p>`;
                    return;
                }
                
                filteredOpportunities.forEach(op => {
                    const isRegistered = registrations.some(r => r.userId === currentUser.id && r.opportunityId === op.id);
                    const isPast = new Date(op.date) < new Date();

                    let statusBadge = '';
                    if (op.status === 'Pendente') {
                        statusBadge = `<span class="absolute top-2 right-2 bg-yellow-400 text-yellow-800 text-xs font-semibold px-2.5 py-0.5 rounded-full">Pendente</span>`;
                    } else if (op.status === 'Concluído' || isPast) {
                        statusBadge = `<span class="absolute top-2 right-2 bg-gray-400 text-gray-800 text-xs font-semibold px-2.5 py-0.5 rounded-full">Concluído</span>`;
                    }

                    const card = `
                        <div class="bg-white rounded-lg shadow-md overflow-hidden transform hover:-translate-y-1 transition-transform duration-300 cursor-pointer relative" data-id="${op.id}">
                            ${statusBadge}
                            <div class="p-6">
                                <div class="flex items-center gap-2 text-sm text-slate-500 mb-2">
                                    <i data-lucide="${op.locationType === 'Online' ? 'monitor' : 'map-pin'}" class="w-4 h-4"></i>
                                    <span>${op.locationType}${op.locationType === 'Presencial' ? ` - ${op.cityCountry}` : ''}</span>
                                </div>
                                <h3 class="text-xl font-bold mb-2">${op.name}</h3>
                                <p class="text-slate-600 text-sm mb-4 line-clamp-3">${op.description}</p>
                                <div class="text-sm text-slate-500">
                                    <p class="font-semibold">ONG: ${op.ong}</p>
                                    <p>${formatDate(op.date)}</p>
                                </div>
                                ${isRegistered ? `<div class="mt-4 text-green-600 font-semibold flex items-center gap-1"><i data-lucide="check-circle" class="w-4 h-4"></i> Inscrito</div>` : ''}
                                ${isAdminMode && op.status === 'Pendente' ? `<button class="approve-btn mt-4 bg-green-500 text-white px-3 py-1 rounded-md text-sm hover:bg-green-600" data-id="${op.id}">Aprovar</button>` : ''}
                            </div>
                        </div>
                    `;
                    opportunitiesList.innerHTML += card;
                });
                lucide.createIcons();
            }

            function renderProfile() {
                document.getElementById('user-name').textContent = currentUser.name;
                
                const upcomingContainer = document.getElementById('upcoming-registrations');
                const pastContainer = document.getElementById('past-registrations');
                upcomingContainer.innerHTML = '';
                pastContainer.innerHTML = '';

                let totalHours = 0;
                const userRegistrations = registrations.filter(r => r.userId === currentUser.id);

                userRegistrations.forEach(reg => {
                    const opportunity = opportunities.find(op => op.id === reg.opportunityId);
                    if (!opportunity) return;
                    
                    if (reg.status === 'Concluído' && reg.hours) {
                        totalHours += reg.hours;
                    }

                    const isPast = new Date(opportunity.date) < new Date();

                    const itemHTML = `
                        <div class="bg-slate-50 p-4 rounded-lg border flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4">
                            <div>
                                <h5 class="font-bold text-lg">${opportunity.name}</h5>
                                <p class="text-sm text-slate-500">${formatDate(opportunity.date)}</p>
                                ${reg.status === 'Concluído' ? `<p class="text-sm font-semibold text-blue-600">Horas registradas: ${reg.hours || 'N/A'}</p>` : ''}
                            </div>
                            <div class="flex-shrink-0 flex gap-2">
                                ${isPast && reg.status !== 'Concluído' ? `<button class="register-hours-btn bg-blue-500 text-white px-3 py-1 rounded-md text-sm" data-reg-id="${reg.id}">Registrar Horas</button>` : ''}
                                ${reg.status === 'Concluído' ? `<button class="testimonial-btn bg-purple-500 text-white px-3 py-1 rounded-md text-sm" data-op-id="${opportunity.id}">Deixar Testemunho</button>` : ''}
                            </div>
                        </div>
                    `;

                    if (isPast || reg.status === 'Concluído') {
                        pastContainer.innerHTML += itemHTML;
                    } else {
                        upcomingContainer.innerHTML += itemHTML;
                    }
                });
                
                currentUser.totalHours = totalHours;
                document.getElementById('user-total-hours').textContent = currentUser.totalHours;

                if (upcomingContainer.innerHTML === '') upcomingContainer.innerHTML = '<p class="text-slate-500">Você não está inscrito em nenhuma oportunidade futura.</p>';
                if (pastContainer.innerHTML === '') pastContainer.innerHTML = '<p class="text-slate-500">Nenhuma participação no histórico.</p>';
            }

            function renderDashboard() {
                const totalHours = registrations.reduce((sum, reg) => sum + (reg.hours || 0), 0);
                const completedOps = opportunities.filter(op => op.status === 'Concluído' || new Date(op.date) < new Date()).length;
                const activeVolunteers = new Set(registrations.map(r => r.userId)).size;

                document.getElementById('total-hours').textContent = totalHours;
                document.getElementById('completed-opportunities').textContent = completedOps;
                document.getElementById('active-volunteers').textContent = activeVolunteers;
            }
            
            function showOpportunityDetails(id) {
                const opportunity = opportunities.find(op => op.id === id);
                if (!opportunity) return;

                const isRegistered = registrations.some(r => r.userId === currentUser.id && r.opportunityId === opportunity.id);
                const isPast = new Date(opportunity.date) < new Date();

                const content = `
                    <h2 class="text-3xl font-bold mb-2">${opportunity.name}</h2>
                    <div class="flex items-center gap-4 text-slate-500 mb-4">
                        <span class="flex items-center gap-1"><i data-lucide="${opportunity.locationType === 'Online' ? 'monitor' : 'map-pin'}" class="w-4 h-4"></i> ${opportunity.locationType}${opportunity.locationType === 'Presencial' ? ` - ${opportunity.cityCountry}` : ''}</span>
                        <span class="flex items-center gap-1"><i data-lucide="calendar" class="w-4 h-4"></i> ${formatDate(opportunity.date)}</span>
                    </div>
                    <p class="text-slate-700 mb-6">${opportunity.description}</p>
                    <div class="bg-slate-100 p-4 rounded-lg">
                        <h4 class="font-bold text-lg mb-2">Sobre a Organização</h4>
                        <p class="font-semibold">${opportunity.ong}</p>
                        <p class="text-sm text-slate-600">Informações adicionais sobre a ONG parceira e seu trabalho na comunidade.</p>
                    </div>
                    <div id="testimonials-section" class="mt-6">
                        <h4 class="font-bold text-lg mb-2">Testemunhos de Voluntários</h4>
                        <!-- Testemunhos aqui -->
                    </div>
                `;
                document.getElementById('details-modal-content').innerHTML = content;
                renderTestimonials(opportunity.id);
                
                const registerBtn = document.getElementById('register-btn');
                registerBtn.dataset.id = id;
                if (isRegistered) {
                    registerBtn.textContent = 'Inscrito';
                    registerBtn.disabled = true;
                    registerBtn.classList.add('bg-green-500', 'cursor-not-allowed');
                    registerBtn.classList.remove('bg-blue-600', 'hover:bg-blue-700');
                } else if (isPast || opportunity.status !== 'Aprovado') {
                    registerBtn.textContent = 'Inscrição Encerrada';
                    registerBtn.disabled = true;
                    registerBtn.classList.add('bg-slate-400', 'cursor-not-allowed');
                    registerBtn.classList.remove('bg-blue-600', 'hover:bg-blue-700');
                } else {
                    registerBtn.textContent = 'Inscrever-se';
                    registerBtn.disabled = false;
                    registerBtn.classList.remove('bg-green-500', 'bg-slate-400', 'cursor-not-allowed');
                    registerBtn.classList.add('bg-blue-600', 'hover:bg-blue-700');
                }

                detailsModal.classList.remove('hidden');
                lucide.createIcons();
            }
            
            function renderTestimonials(opportunityId) {
                const container = document.getElementById('testimonials-section');
                const relevantTestimonials = testimonials.filter(t => t.opportunityId === opportunityId);

                if (relevantTestimonials.length === 0) {
                    container.innerHTML += '<p class="text-sm text-slate-500">Ainda não há testemunhos para esta oportunidade.</p>';
                    return;
                }
                
                let testimonialsHTML = '';
                relevantTestimonials.forEach(test => {
                    const user = { name: 'Voluntário Anônimo' }; // Simulação, idealmente buscaria o nome do usuário
                    testimonialsHTML += `
                        <div class="border-t pt-4 mt-4">
                            ${test.photoUrl ? `<img src="${test.photoUrl}" onerror="this.onerror=null;this.src='https://placehold.co/600x400/e2e8f0/475569?text=Imagem+Indispon%C3%ADvel';" alt="Foto do testemunho" class="rounded-lg mb-2 w-full h-48 object-cover">` : ''}
                            <blockquote class="text-slate-600 italic">"${test.text}"</blockquote>
                            <p class="text-right font-semibold text-sm mt-2">- ${user.name}</p>
                        </div>
                    `;
                });
                container.innerHTML += testimonialsHTML;
            }

            // --- FUNÇÕES DE NAVEGAÇÃO E UI ---
            function navigateTo(hash) {
                pages.forEach(page => {
                    if (`#${page.id}` === hash) {
                        page.classList.add('active');
                    } else {
                        page.classList.remove('active');
                    }
                });
                // Atualiza o estado visual dos links de navegação
                navLinks.forEach(link => {
                    if (link.getAttribute('href') === hash) {
                        link.classList.add('bg-blue-600', 'text-white');
                        link.classList.remove('text-gray-700');
                    } else {
                        link.classList.remove('bg-blue-600', 'text-white');
                        link.classList.add('text-gray-700');
                    }
                });

                // Renderiza o conteúdo da página ativa
                if (hash === '#perfil') renderProfile();
                if (hash === '#impacto') renderDashboard();
                if (hash === '#oportunidades') renderOpportunities();
            }
            
            function showMessage(text, type = 'success') {
                const messageBox = document.getElementById('message-box');
                const messageText = document.getElementById('message-text');
                
                messageText.textContent = text;
                messageBox.className = 'fixed top-5 right-5 text-white px-6 py-3 rounded-lg shadow-lg transform transition-transform duration-300 z-50'; // Reset classes
                if (type === 'success') {
                    messageBox.classList.add('bg-green-500');
                } else {
                    messageBox.classList.add('bg-red-500');
                }
                
                messageBox.classList.remove('translate-x-[120%]');
                
                setTimeout(() => {
                    messageBox.classList.add('translate-x-[120%]');
                }, 3000);
            }

            // --- EVENT LISTENERS ---
            
            // Navegação
            navLinks.forEach(link => {
                link.addEventListener('click', (e) => {
                    e.preventDefault();
                    const hash = e.target.getAttribute('href');
                    window.location.hash = hash;
                });
            });
            
            window.addEventListener('hashchange', () => {
                const hash = window.location.hash || '#oportunidades';
                navigateTo(hash);
            });

            // Filtros e Busca
            searchInput.addEventListener('input', renderOpportunities);
            filterLocal.addEventListener('change', renderOpportunities);
            
            // Abrir/Fechar Modals
            document.getElementById('create-opportunity-btn').addEventListener('click', () => createModal.classList.remove('hidden'));
            document.getElementById('close-create-modal').addEventListener('click', () => createModal.classList.add('hidden'));
            document.getElementById('close-details-modal').addEventListener('click', () => detailsModal.classList.add('hidden'));
            document.getElementById('close-hours-modal').addEventListener('click', () => hoursModal.classList.add('hidden'));
            document.getElementById('close-testimonial-modal').addEventListener('click', () => testimonialModal.classList.add('hidden'));

            // Ações nos cards
            opportunitiesList.addEventListener('click', (e) => {
                const card = e.target.closest('div[data-id]');
                const approveBtn = e.target.closest('.approve-btn');

                if (approveBtn) {
                    const id = parseInt(approveBtn.dataset.id);
                    const opportunity = opportunities.find(op => op.id === id);
                    if (opportunity) {
                        opportunity.status = 'Aprovado';
                        showMessage(`Oportunidade "${opportunity.name}" aprovada!`);
                        renderOpportunities();
                    }
                } else if (card) {
                    const id = parseInt(card.dataset.id);
                    showOpportunityDetails(id);
                }
            });

            // Ações nos Modals
            document.getElementById('register-btn').addEventListener('click', (e) => {
                const id = parseInt(e.target.dataset.id);
                registrations.push({
                    id: registrations.length + 1,
                    userId: currentUser.id,
                    opportunityId: id,
                    status: 'Inscrito',
                    hours: null
                });
                detailsModal.classList.add('hidden');
                showMessage('Inscrição realizada com sucesso!');
                renderOpportunities();
            });
            
            document.getElementById('create-opportunity-form').addEventListener('submit', (e) => {
                e.preventDefault();
                const formData = new FormData(e.target);
                const newOpportunity = {
                    id: opportunities.length + 1,
                    name: formData.get('name'),
                    description: formData.get('description'),
                    ong: formData.get('ong'),
                    locationType: formData.get('locationType'),
                    cityCountry: formData.get('cityCountry'),
                    date: formData.get('date'),
                    status: 'Pendente'
                };
                opportunities.push(newOpportunity);
                e.target.reset();
                createModal.classList.add('hidden');
                showMessage('Oportunidade enviada para aprovação!');
                renderOpportunities();
            });
            
            document.getElementById('hours-form').addEventListener('submit', (e) => {
                e.preventDefault();
                const regId = parseInt(e.target.dataset.regId);
                const hours = parseInt(document.getElementById('hours-input').value);
                
                const registration = registrations.find(r => r.id === regId);
                if (registration) {
                    registration.hours = hours;
                    registration.status = 'Concluído';
                    showMessage('Horas registradas com sucesso!');
                    hoursModal.classList.add('hidden');
                    renderProfile();
                }
            });
            
            document.getElementById('testimonial-form').addEventListener('submit', (e) => {
                e.preventDefault();
                const opId = parseInt(e.target.dataset.opId);
                const text = document.getElementById('testimonial-text').value;
                const photoUrl = document.getElementById('testimonial-photo').value;
                
                testimonials.push({
                    id: testimonials.length + 1,
                    userId: currentUser.id,
                    opportunityId: opId,
                    text: text,
                    photoUrl: photoUrl
                });
                
                e.target.reset();
                testimonialModal.classList.add('hidden');
                showMessage('Testemunho publicado! Obrigado por compartilhar.');
            });

            // Ações no perfil
            document.getElementById('perfil').addEventListener('click', (e) => {
                if (e.target.classList.contains('register-hours-btn')) {
                    const regId = parseInt(e.target.dataset.regId);
                    const registration = registrations.find(r => r.id === regId);
                    const opportunity = opportunities.find(op => op.id === registration.opportunityId);
                    document.getElementById('hours-opportunity-name').textContent = opportunity.name;
                    document.getElementById('hours-form').dataset.regId = regId;
                    hoursModal.classList.remove('hidden');
                }
                if (e.target.classList.contains('testimonial-btn')) {
                    const opId = parseInt(e.target.dataset.opId);
                    const opportunity = opportunities.find(op => op.id === opId);
                    document.getElementById('testimonial-opportunity-name').textContent = opportunity.name;
                    document.getElementById('testimonial-form').dataset.opId = opId;
                    testimonialModal.classList.remove('hidden');
                }
            });
            
            // Admin Mode
            document.getElementById('admin-toggle').addEventListener('change', (e) => {
                isAdminMode = e.target.checked;
                renderOpportunities();
            });

            // Mobile Menu
            const mobileMenuButton = document.getElementById('mobile-menu-button');
            const mobileMenu = document.getElementById('mobile-menu');
            mobileMenuButton.addEventListener('click', () => {
                mobileMenu.classList.toggle('hidden');
            });
            mobileMenu.addEventListener('click', () => {
                mobileMenu.classList.add('hidden');
            });

            // --- INICIALIZAÇÃO ---
            const initialHash = window.location.hash || '#oportunidades';
            navigateTo(initialHash);
        });
    </script>
</body>
</html>
