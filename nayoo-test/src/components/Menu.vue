<template>
  <div id='Menu'>
    <nav class="navbar navbar-expand-xl navbar-light shadow">
        <ul class="navbar-nav justify-content-center container-fluid">
                    <li class="nav-item">
                      <a class="nav-link active h3 mb-0" href="#">LOGO</a>
                    </li>
                      <div class="input-group w-25">
                          <span class="input-group-text rounded-left pl-4 pr-0" id="basic-addon1">
                              <svg xmlns="http://www.w3.org/2000/svg" width="12" height="12" fill="currentColor" class="bi bi-search" viewBox="0 0 16 16">
                              <path d="M11.742 10.344a6.5 6.5 0 1 0-1.397 1.398h-.001c.03.04.062.078.098.115l3.85 3.85a1 1 0 0 0 1.415-1.414l-3.85-3.85a1.007 1.007 0 0 0-.115-.1zM12 6.5a5.5 5.5 0 1 1-11 0 5.5 5.5 0 0 1 11 0z"/>
                              </svg>
                          </span>
                          <input type="search" class="form-control rounded-right fluid" placeholder="ค้นหา" aria-label="Input group example" aria-describedby="basic-addon1" size="100" style="padding: 10px:">
                      </div>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                    <li class="nav-item">
                      <a class="nav-link text-dark mx-4 weight" href="#">หน้าแรก</a>
                    </li>
                    <li class="nav-item">
                      <a class="nav-link text-dark mx-4 weight" href="#">เกี่ยวกับ</a>
                    </li>
                    <li class="nav-item">
                      <a class="nav-link text-dark weight" href="#">ติดต่อ</a>
                    </li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                    <li class="nav-item">
                      <button type="button" class="btn btn-secondary btn-sm text-dark weight">Register</button>
                    </li>
                    <li class="nav-item">
                      <button type="button" class="btn btn-outline-dark btn-sm weight">Sign in</button>
                    </li>
        </ul>
    </nav>
  </div>
</template>

<script>
export default {
  name: 'Menu',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
input {
  width: 1000px;
  height: 30px;
  background-color: #E5E5E5;
  border: none;
}
span {
  background-color: #E5E5E5;
  border: none;
  border-right-color: #E5E5E5;
}
.btn-secondary {
  background-color: #E5E5E5;
  border: none;
}

.weight {
  font-weight: 700;
}
</style>
