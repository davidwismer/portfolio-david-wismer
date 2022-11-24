<script>
</script>

<template>
    <section class="about-content">
        <div class="presentation">
            <div class="top-line">
                Hi, my name is <strong class="name">David
                    Wismer</strong>.</div>
            <div class="core-line">I'm a Media engineering student at the HEIG-VD
                who aspires to become a web developer.
            </div>
        </div>
        <div class="links">
            <a class="linkedin" href="https://www.linkedin.com/in/david-wismer-25ba29200/" target="_blank">
                <div class="linkText">Go to Linkedin</div>
                <font-awesome-icon icon="fab fa-linkedin" />
            </a>
            <a class="github" href="https://github.com/davidwismer" target="_blank">
                <div class="linkText">Go to Github</div>
                <font-awesome-icon icon="fab fa-github" />
            </a>
        </div>
    </section>
</template>

<style scoped>
section {
    position: fixed;
    width: 100%;
    height: 100%;
}

.presentation {
    position: relative;
    width: 500px;
    text-align: left;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
}

.top-line {
    font-size: 24px;
}

.core-line {
    font-size: 24px;
    font-family: "League Spartan Regular";
}

.name {
    font-size: 32px;
    color: #ACBABF;
}

.links {
    position: fixed;
    top: 50%;
    transform: translate(0, -50%);
    display: flex;
    flex-direction: column;
    gap: 20px;
}

svg {
    font-size: 50px;
    margin-right: 15px;
}

.linkText {
    opacity: 0;
    transition: 0.4s;
    margin-left: 10px;
}

a {
    border-radius: 0 5px 5px 0;
    display: flex;
    justify-content: flex-end;
    align-items: center;
    text-decoration: none;
    width: 75px;
    height: 75px;
    color: #565656;
    background-color: #C0C0C2;
    transition: 0.4s;
}

@media screen and (min-width: 450px) {
    a:hover {
        width: 150px;
    }

    a:hover div {
        opacity: 1;
        transition: 1s;
    }
}

@media screen and (max-width: 450px) {
    .presentation {
        width: 90%;
    }

    .core-line,
    .top-line {
        font-size: 18px;
    }

    .name {
        font-size: 20px;
    }

    .links {
        top: 100%;
        left: 50%;
        transform: translate(-50%, -100%);
        flex-direction: row;
    }

    a {
        border-radius: 5px 5px 0 0;
    }
}
@media screen and (max-width: 700px){
    .presentation {
        width: 300px;
    }
}
</style>