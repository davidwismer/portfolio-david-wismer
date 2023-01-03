<script setup>

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
            <div class="core-line contact">david@thewismer.ch | +41786952822
            </div>
            <a href="/assets/Resume.pdf" target="_blank" class="resume">RESUME</a>
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
    margin-bottom: 15px;
}

.core-line {
    font-size: 24px;
    font-family: "League Spartan Regular";
    margin-bottom: 15px;
}

.contact {
    font-size: 20px;
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
    gap: 10px;
}

a {
    text-decoration: none;
    color: #565656;
    background-color: #C0C0C2;
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

.linkedin,
.github {
    border-radius: 0 5px 5px 0;
    display: flex;
    justify-content: flex-end;
    align-items: center;
    width: 75px;
    height: 75px;
    transition: 0.4s;
}

.linkedin {
    background-color: #0077B5;
    color: white;
}

.github {
    background-color: #333;
    color: #f5f5f5;
}

.resume {
    display: inline-block;
    position: relative;
    left: 50%;
    transform: translate(-50%, 0);
    color: #ACBABF;
    background-color: #373737;
    text-align: center;
    padding: 10px 10px 10px 10px;
    font-family: "League Spartan Regular";
    border: 1px solid #ACBABF;
    font-size: 20px;
    margin-top: 15px;
    transition: 0.4s;
}

@media screen and (min-width: 450px) {

    .linkedin:hover,
    .github:hover {
        width: 150px;
    }

    a:hover div {
        opacity: 1;
        transition: 1s;
    }

    .resume:hover {
        background-color: #ACBABF;
        color: #373737;
        scale: 1.2;
        transform: translate(-40%, 0);
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

    .linkedin,
    .github {
        border-radius: 5px 5px 0 0;
    }

    .resume {
        scale: 0.8;
    }
}

@media screen and (max-width: 700px) {
    .presentation {
        width: 300px;
    }
}
</style>