<script setup>
    import { computed } from 'vue'

    const copyright = computed(() =>{
        const currentYear = new Date().getFullYear()
        return `© Copyright ${currentYear} | Jeremy Pélage`
    });
</script>

<template>
    <footer class="footer">
        <div class="footer__content">
            <div class="footer__adress">
                <h3>Mes contacts</h3>
                <address>
                    <a href="mailto:jeremy.pelage@outlook.com">jeremy.pelage@outlook.com</a>
                    <a href="tel:+0695458872">06.95.45.88.72</a>
                    <p>Grand Couronne 76530</p>
                </address>
            </div>
            <div class="footer__borderRight"></div>
            <div class="footer__social">
                <h3>Me retrouver</h3>
                <a class="footer__social__icon" href="https://github.com/GLuck777" target="_blank" rel="noopener noreferrer">
                    <img src="@/assets/images/gitHub.png" alt="Logo GitHub">
                </a>
                <a class="footer__social__icon" href="https://www.linkedin.com/in/jeremy-pelage-1b5417150/" target="_blank" rel="noopener noreferrer">
                    <img src="@/assets/images/linkedin.ico" alt="Logo LinkedIn">
                </a>
                <a class="footer__social__icon" href="https://www.instagram.com/iam_ianblack/" target="_blank" rel="noopener noreferrer">
                    <img src="@/assets/images/instagram.png" alt="Logo Instagram">
                </a>
            </div>
        </div>
        <div class="footer__copyright">
            <p>Dernières modifications le<time datetime="2024-04-17">6 novembre 2024</time></p>
            <p class="copyright">{{ copyright }}</p>
        </div>
    </footer>
</template>

<style scoped>
    .footer__content {
        display: flex;
        justify-content: space-evenly;
    }

    footer * {
        background-color: #060640;
        color: white;
        padding: 10px;
    }
    
    .footer__borderRight {
        /* border-right: 1px solid #EFFAFD; */
        border-right: 1px solid #4651f0bd;
    }

    address {
        display: flex;
        flex-direction: column;
    }

    .footer__copyright {
        text-align: center;
    }

    time {
        font-style: italic;
    }

    .copyright {
        font-style: italic;
        font-size: 0.8em;
    }

    .footer__social__icon:hover {
        opacity: 50%;
    }
</style>