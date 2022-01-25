<template>
    <div>
        <div class="row">
            <div class="col-md-4">
              <div class="card" style="width: 18em:">
                <img class="card-img-top" src>
                <ul class="list-group list-group-flush">
                    <li class="list-group-item">repositorios:
                        <span class="">{{user.public_repos}}</span>
                    </li>
                    <li class="list-group-item">seguidores:
                        <span class="">{{user.followers}}</span>
                    </li>
                    <li class="list-group-item">segindo:
                        <span class="">{{user.following}}</span>
                    </li>
                </ul>
                <div class="card-body">
                    <a :href="user.html_url" class="btn btn-warning btn-block"> ver perfil</a>
                </div>
              </div>
            </div> 
        </div>
    </div>
</template>
<script>
    export default{
        props:["user"]
    }
</script>