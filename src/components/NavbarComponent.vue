<!-- Navbar Component -->
<template>
	<nav class="navbar navbar-expand-lg navbar-dark bg-dark">
        <div class ="container">
        <a class="navbar-brand" href="/index.html">ar&chi;ain</a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarResponsive" aria-controls="navbarResponsive" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse justify-content-end" id="navbarResponsive">
            <ul class="navbar-nav nav-fill">
			<li class="nav-item">
                <a class="nav-link" v-bind:class="{active: isSubmit}" 
                  @click="changeView('paper-submit')" 
                  href="#">Submit a paper
              </a>
			</li>
            <li class="nav-item">
                <a class="nav-link" v-bind:class=" {active: isComment} "
                @click="changeView('paper-comments')"
                href="#">Review a paper
              </a>
			</li>
			<li class="nav-item">
                <a class="nav-link" v-bind:class=" {active: isRevise} "
                  @click="changeView('paper-amend');"
                  href="#">Revise a paper
              </a>
			</li>
			<li class="nav-item">
                <a class="nav-link" v-bind:class=" {active: isCheck} "
                 @click="changeView('paper-status')"
                 href="#">Check blockchain
              </a>
			</li>
            </ul>
		</div><!--/.navbar-collapse -->
        </div>
	</nav>
</template>

<script>
    const ACTIVE_SUBMIT = 'paper-submit', ACTIVE_REVISE = 'paper-amend';
    const ACTIVE_CHECK = 'paper-status', ACTIVE_COMMENT = 'paper-comments';

    module.exports = {
        props: ['initialActive'],
        data(){
            return {
                currentActive: this.initialActive
            }
        },
        methods: {
            changeView: function(newView) {
                this.$emit('update:view',newView);
                this.currentActive = newView;
            }
        },
        computed: {
            isSubmit() {
                return this.currentActive === ACTIVE_SUBMIT;
            },
            isRevise() {
                return this.currentActive === ACTIVE_REVISE;
            },
            isCheck() {
                return this.currentActive === ACTIVE_CHECK;
            },
            isComment() {
                return this.currentActive === ACTIVE_COMMENT;
            },
        }
    }
</script>


<style scoped>

</style>
