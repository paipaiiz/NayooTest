<template>
  <div class="api">
    <div class="h2">API CRUD</div>
    <div class="d-flex justify-content-start">
      <button
        type="button"
        class="btn btn-success"
        data-bs-toggle="modal"
        data-bs-target="#createupdate"
        @click="addClick()"
      >
        <i class="bi bi-plus-square-dotted"></i> สร้าง
      </button>
    </div>
    <br />
    <div>
      <table class="table">
        <thead>
          <tr>
            <th scope="col">ไอดี</th>
            <th scope="col">รูป</th>
            <th scope="col">ชื่อ</th>
            <th scope="col">เบอร์โทรศัพท์มือถือ</th>
            <th scope="col">ตัวเลือก</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="list in lists" :key="list.id">
            <th scope="row">{{ list.id }}</th>
            <td>
              <img
                v-if="list.image != null"
                :src="`https://test-frontend-api.nayoo.co/images/avatars/${list.image}`"
                width="25px"
                class="rounded-circle"
                alt="name"
              />
              <img
                v-else
                src="https://www.nicepng.com/png/full/128-1280406_view-user-icon-png-user-circle-icon-png.png"
                width="25px"
                class="rounded-circle"
                alt="name"
              />
            </td>
            <td>{{ list.name }}</td>
            <td>{{ list.mobilenumber }}</td>
            <td>
              <div class="col">
                <a
                  type="button"
                  class="btn btn-link"
                  data-bs-toggle="modal"
                  data-bs-target="#showID"
                  @click="showID(list)"
                  ><i class="bi bi-search"></i
                ></a>
                <a
                  type="button"
                  class="btn btn-link"
                  data-bs-toggle="modal"
                  data-bs-target="#createupdate"
                  @click="editClick(list)"
                  ><i class="bi bi-pencil-square"></i
                ></a>
                <a
                  type="button"
                  class="btn btn-link"
                  @click="deleteClick(list.id)"
                  ><i class="bi bi-trash"></i
                ></a>
              </div>
            </td>
          </tr>
        </tbody>
      </table>
    </div>

    <!-- Modal Create&&Update -->
    <div
      class="modal fade"
      id="createupdate"
      tabindex="-1"
      aria-labelledby="exampleModalLabel"
      aria-hidden="true"
    >
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">{{ modalTitle }}</h5>
            <button
              type="button"
              class="btn-close"
              data-bs-dismiss="modal"
              aria-label="Close"
            ></button>
          </div>
          <div class="modal-body" align="left">
            <form>
              <div class="form-group">
                <label for="exampleInputName">ชื่อ</label>
                <input
                  type="text"
                  class="form-control mb-3"
                  id="exampleInputName"
                  placeholder="กรอกชื่อ"
                  v-model="name"
                />
              </div>
              <div class="form-group">
                <label for="exampleInputOrganization">ชื่อองค์กร</label>
                <input
                  type="text"
                  class="form-control mb-3"
                  id="exampleInputOrganization"
                  placeholder="กรอกชื่อองค์กร"
                  v-model="organization"
                />
              </div>
              <div class="form-group">
                <label for="exampleInputMobilenumber"
                  >เบอร์โทรศัพท์มือถือ</label
                >
                <input
                  type="text"
                  class="form-control mb-3"
                  id="exampleInputMobilenumber"
                  placeholder="กรอกเบอร์โทรศัพท์มือถือ"
                  v-model="mobilenumber"
                />
              </div>
              <div class="form-group">
                <label for="exampleInputHomephone">เบอร์บ้าน</label>
                <input
                  type="text"
                  class="form-control mb-3"
                  id="exampleInputHomephone"
                  placeholder="กรอกเบอร์บ้าน"
                  v-model="homephone"
                />
              </div>
              <div class="form-group">
                <label for="exampleInputOfficenumber">เบอร์ที่ทำงาน</label>
                <input
                  type="text"
                  class="form-control mb-3"
                  id="exampleInputOfficenumber"
                  placeholder="กรอกเบอร์ที่ทำงาน"
                  v-model="officenumber"
                />
              </div>
              <div class="form-group">
                <label for="exampleInputEmail1">อีเมล</label>
                <input
                  type="email"
                  class="form-control mb-3"
                  id="exampleInputEmail1"
                  placeholder="กรอกอีเมล"
                  v-model="email"
                />
              </div>
              <div class="p-2 w-50 bd-highlight">
                <img
                  v-show="id != 0"
                  width="50px"
                  height="50px"
                  :src="`https://test-frontend-api.nayoo.co/images/avatars/${image_api}`"
                />
                <img
                  id="output"
                  v-show="id == 0 && image != null"
                  width="50px"
                  height="50px"
                />
                <input
                  class="m-2"
                  type="file"
                  v-if="id == 0"
                  ref="fileInput"
                  @change="imageUpload"
                />
              </div>
            </form>
          </div>
          <div class="modal-footer">
            <button
              type="button"
              class="btn btn-primary"
              data-bs-dismiss="modal"
              v-if="id == 0"
              @click="createClick()"
            >
              สร้างรายชื่อ
            </button>
            <button
              type="button"
              class="btn btn-primary"
              data-bs-dismiss="modal"
              v-if="id != 0"
              @click="updateClick()"
            >
              อัพเดทรายชื่อ
            </button>
          </div>
        </div>
      </div>
    </div>

    <!-- Modal ShowID-->
    <div
      class="modal fade"
      id="showID"
      tabindex="-1"
      aria-labelledby="exampleModalLabel"
      aria-hidden="true"
    >
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">รายละเอียด</h5>
            <button
              type="button"
              class="btn-close"
              data-bs-dismiss="modal"
              aria-label="Close"
            ></button>
          </div>
          <div class="modal-body" align="left">
            <div class="card" style="width: 29rem">
              <img
                v-if="image != null"
                :src="`https://test-frontend-api.nayoo.co/images/avatars/${image}`"
                class="card-img-top"
                alt="name"
              />
              <img
                v-else
                src="https://www.nicepng.com/png/full/128-1280406_view-user-icon-png-user-circle-icon-png.png"
                class="card-img-top"
                alt="name"
              />
              <div class="card-body">
                <h5 class="card-title">{{ name }}</h5>
                <p class="card-text">{{ organization }}</p>
                <div class="row">
                  <small>เบอร์โทรศัพท์มือถือ: {{ mobilenumber }}</small>
                  <small>เบอร์บ้าน: {{ homephone }}</small>
                  <small>เบอร์ที่ทำงาน: {{ officenumber }}</small>
                  <small>อีเมล: {{ email }}</small>
                </div>
              </div>
            </div>
          </div>
          <div class="modal-footer">
            <button
              type="button"
              class="btn btn-danger"
              data-bs-dismiss="modal"
            >
              ปิด
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "api",
  data() {
    return {
      msg: "",
      lists: [],
      modalTitle: "",
      id: 0,
      name: "",
      organization: "",
      mobilenumber: "",
      homephone: "",
      officenumber: "",
      email: "",
      image: null,
      image_api: null,
    };
  },
  methods: {
    showAll() {
      this.axios
        .get(`https://test-frontend-api.nayoo.co/api/Nayoo/1101/index`)
        .then((response) => {
          this.msg = response.data.message;
          this.lists = response.data.data;
          console.log(this.msg);
        })
        .catch((error) => {
          console.log(error);
        });
    },
    showID(list) {
      this.axios
        .get(`https://test-frontend-api.nayoo.co/api/Nayoo/1101/show/${list}`)
        .then((response) => {
          this.msg = response.data.status;
          this.id = list.id;
          this.name = list.name;
          this.organization = list.organization;
          this.mobilenumber = list.mobilenumber;
          this.homephone = list.homephone;
          this.officenumber = list.officenumber;
          this.email = list.email;
          this.image = list.image;
          console.log(this.msg);
        })
        .catch((error) => {
          console.log(error);
        });
    },
    addClick() {
      this.modalTitle = "สร้างรายชื่อ";
      this.id = 0;
      this.name = "";
      this.organization = "";
      this.mobilenumber = "";
      this.homephone = "";
      this.officenumber = "";
      this.email = "";
      this.image = null;
      this.image_api = null;
      const input = this.$refs.fileInput;
      input.type = "text";
      input.type = "file";
    },
    editClick(list) {
      this.modalTitle = "แก้ไขรายชื่อ";
      this.id = list.id;
      this.name = list.name;
      this.organization = list.organization;
      this.mobilenumber = list.mobilenumber;
      this.homephone = list.homephone;
      this.officenumber = list.officenumber;
      this.email = list.email;
      this.image_api = list.image;
    },
    createClick() {
      let formData = new FormData();
      let name = this.name;
      let organization = this.organization;
      let mobilenumber = this.mobilenumber;
      let homephone = this.homephone;
      let officenumber = this.officenumber;
      let email = this.email;

      let img = this.image;
      formData.append("name", name);
      formData.append("organization", organization);
      formData.append("mobilenumber", mobilenumber);
      formData.append("homephone", homephone);
      formData.append("officenumber", officenumber);
      formData.append("email", email);
      formData.append("image", img);
      this.axios
        .post(
          `https://test-frontend-api.nayoo.co/api/Nayoo/1101/store`,
          formData,
          {
            headers: {
              "Content-Type": "multipart/form-data",
            },
          }
        )
        .then((response) => {
          this.showAll();
          alert(response.data.message);
        })
        .catch((error) => {
          alert(error);
          console.log(error);
        });
    },
    updateClick() {
      this.axios
        .put(
          `https://test-frontend-api.nayoo.co/api/Nayoo/1101/update/${this.id}`,
          {
            name: this.name,
            organization: this.organization,
            mobilenumber: this.mobilenumber,
            homephone: this.homephone,
            officenumber: this.officenumber,
            email: this.email,
          }
        )
        .then((response) => {
          this.showAll();
          alert(response.data.message);
        });
    },
    deleteClick(list) {
      if (!confirm("Are you sure?")) {
        return;
      }
      this.axios
        .delete(
          `https://test-frontend-api.nayoo.co/api/Nayoo/1101/destroy/${list}`
        )
        .then((response) => {
          console.log(response.data);
          // alert(response.data);
          this.showAll();
        })
        .catch((error) => {
          alert(error);
          console.log(error);
        });
    },
    imageUpload(event) {
      console.log(event);
      this.image = event.target.files[0];
      var output = document.getElementById("output");
      output.src = URL.createObjectURL(event.target.files[0]);
      output.onload = function () {
        URL.revokeObjectURL(output.src); // free memory
      };
    },
  },
  mounted() {
    this.showAll();
  },
};
</script>

<style></style>
