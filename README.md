# ADEAN
NAMING VOTE
<script>
    let selectedButton = null;
    const votes = {
        'ADEAN': 0,
        'AEVA': 0,
        'LYRA': 0,
        'LUMEX': 0,
        'AEON': 0,
        'ALBA': 0,
        'NOVA': 0,
        'SEMA': 0,
        'PRIMA': 0,
        'NEXUS': 0,
        'GERMEN': 0,
        'ORIGO': 0
    };
    
    function toggleSelection(name, button) {
        if (selectedButton) {
            selectedButton.classList.remove('selected');
            selectedButton.textContent = `Selecionar (${votes[name]} votos)`;
        }
        
        if (selectedButton !== button) {
            votes[name]++;
            button.classList.add('selected');
            button.textContent = `Selecionado (${votes[name]} votos)`;
            selectedButton = button;
            showNotification(name);
        } else {
            votes[name]--;
            selectedButton = null;
            button.textContent = `Selecionar (${votes[name]} votos)`;
            hideNotification();
        }

        // Atualiza todos os botões com seus respectivos números de votos
        updateAllVoteCounts();
    }
    
    function updateAllVoteCounts() {
        const buttons = document.querySelectorAll('.button');
        buttons.forEach(button => {
            const name = button.getAttribute('data-name');
            if (button !== selectedButton) {
                button.textContent = `Selecionar (${votes[name]} votos)`;
            }
        });
    }
    
    function showNotification(name) {
        const notification = document.getElementById('notification');
        notification.textContent = `Você selecionou: ${name} (${votes[name]} votos)`;
        notification.style.display = 'block';
    }
    
    function hideNotification() {
        const notification = document.getElementById('notification');
        notification.style.display = 'none';
    }

    // Inicializa os contadores em todos os botões
    document.addEventListener('DOMContentLoaded', function() {
        const buttons = document.querySelectorAll('.button');
        buttons.forEach(button => {
            const name = button.getAttribute('onclick').match(/'([^']+)'/)[1];
            button.setAttribute('data-name', name);
            button.textContent = `Selecionar (0 votos)`;
        });
    });
</script>
