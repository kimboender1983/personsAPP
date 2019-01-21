<template>
    <div>
        <b-navbar toggleable="md" type="dark" variant="primary">

            <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>

            <b-navbar-brand  to="/">Persons</b-navbar-brand>

            <b-collapse is-nav id="nav_collapse">

                <b-navbar-nav>
                    <!-- <b-nav-item href="#">Add</b-nav-item> -->
                    <b-link style="color:white;" to="/add" tag="b-nav-item">Add</b-link>
                </b-navbar-nav>

                <!-- Right aligned nav items -->
                <b-navbar-nav class="ml-auto">
                    Right aligned stuff
                </b-navbar-nav>

            </b-collapse>
        </b-navbar>
    </div>
</template>

<script>



export default {

}
</script>

