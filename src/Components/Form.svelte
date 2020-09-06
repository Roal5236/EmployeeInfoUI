
            <script>
                import { createEventDispatcher } from 'svelte';

                const dispatch = createEventDispatcher();

                function togglePopup() {
                    dispatch('message', {
                     text: 'popup'
                    });
                }

                function saveData() {
                    alert("hello world");
                    dispatch('message', {
                     text: 'save',
                     fname: document.getElementById('fname').value,
                     lname: document.getElementById('lname').value,
                     phone: document.getElementById('phone').value,
                     company: document.getElementById('company').value,
                     email: document.getElementById('email').value,

                    });

                
                }
                function saveAndNewData() {
                    dispatch('message', {
                     text: 'saveNew',
                     fname: document.getElementById('fname').value,
                     lname: document.getElementById('lname').value,
                     phone: document.getElementById('phone').value,
                     company: document.getElementById('company').value,
                     email: document.getElementById('email').value,

                    });
                     document.getElementById('fname').value="";
                     document.getElementById('lname').value="";
                      document.getElementById('phone').value="";
                      document.getElementById('company').value="";
                      document.getElementById('email').value="";
                }
            
            </script>

            
            
            
            <div class="form-container col" style="background-color:white;">
                <div class="form-info">
                    <h1 class="form-title">Employee Information</h1>
                    <p class="form-sub-title">More details about the employee and their roles</p>
                </div>

                <div class="form-data">
                    <p class="form-input-title">Employee First Name</p>
                    <input class="form-input" id='fname'/>
                </div>

                <div class="form-data">
                    <p class="form-input-title">Employee Last Name</p>
                    <input class="form-input" id='lname'/>
                </div>

                <div class="form-data">
                    <p class="form-input-title">Employee Phone No.</p>
                    <input class="form-input" id='phone'/>
                </div>

                <div class="form-data">
                    <p class="form-input-title">Company</p>
                    <input class="form-input" id='company'/>
                </div>

                <div class="form-data">
                    <p class="form-input-title">Employee Personal Email</p>
                    <input class="form-input" id='email'/>
                </div>

                <!-- <div class="form-data">
                    <p class="form-option">Offices can be one person or multiple a single person can dill in these roles too.
                    You can also selece a director name from the drop down list</p>
                </div> -->

                <div class="button-holder">
                    <p class="bottom-button save" on:click={() => saveData()}>SAVE</p>
                    <p class="bottom-button cancel" on:click={() => togglePopup()}>CANCEL</p>
                    <p class="bottom-button newSave " on:click={() => saveAndNewData()}>SAVE & NEW</p>
                </div>
            </div>
        
    