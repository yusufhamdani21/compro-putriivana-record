<template>
    <footer>
        <div class="footer-left">
            <span class="logo">Putri Ivana Record</span>
            <p>Label musik independen dari Indonesia.</p>
        </div>
        <div class="footer-right">
            <RouterLink to="/privacy-policy">Privacy Policy</RouterLink>
            <p>© {{ year }} Putri Ivana Record. All rights reserved.</p>
        </div>
    </footer>
</template>

<script setup>
const year = new Date().getFullYear()
</script>

<style scoped>
footer {
    position: relative;
    z-index: 1;
    border-top: 1px solid rgba(46, 116, 232, 0.1);
    padding: 32px 60px;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.footer-left {
    display: flex;
    flex-direction: column;
    gap: 6px;
}

.logo {
    font-family: var(--font-display);
    font-size: 1.15rem;
    font-weight: 400;
}

.footer-left p,
.footer-right p {
    font-size: 0.75rem;
    color: var(--text-muted);
}

.footer-right {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    gap: 6px;
}

.footer-right a {
    font-size: 0.75rem;
    color: var(--blue-sky);
    transition: color var(--transition);
}

.footer-right a:hover {
    color: var(--white);
}

@media (max-width: 768px) {
    footer {
        padding: 28px 24px;
        flex-direction: column;
        gap: 16px;
        text-align: center;
    }

    .footer-right {
        align-items: center;
    }
}
</style>