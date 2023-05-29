<template>
    <div>
        <div class="fixed top-0 right-0 p-4">
            <button @click="signout"
                class="bg-white hover:bg-gray-100 text-gray-800 font-semibold py-2 px-4 border border-gray-400 rounded shadow">
                Déconnexion
            </button>
        </div>
        <div class="">
            <div class="flex flex-col items-center justify-center min-h-screen py-4">
                <button @click="signInWithGoogle"
                    class="bg-white hover:bg-gray-100 text-gray-800 font-semibold py-2 px-4 border border-gray-400 rounded shadow mb-4">
                    <img class="inline-block h-6 w-6 mr-2" src="~/assets/images/google-logo.png" alt="Google logo">
                    Se connecter avec Google
                </button>
                <button @click="signInWithFacebook"
                    class="bg-white hover:bg-gray-100 text-gray-800 font-semibold py-2 px-4 border border-gray-400 rounded shadow mb-4">
                    <img class="inline-block h-6 w-6 mr-2" src="~/assets/images/facebook-logo.png" alt="Facebook logo">
                    Se connecter avec Facebook
                </button>
                <button @click="signInWithLinkedIn"
                    class="bg-white hover:bg-gray-100 text-gray-800 font-semibold py-2 px-4 border border-gray-400 rounded shadow mb-4">
                    <img class="inline-block h-6 w-6 mr-2" src="~/assets/images/linkedin-logo.png" alt="Apple logo">
                    Se connecter avec LinkedIn
                </button>
            </div>
        </div>
    </div>
</template>
   
<script setup>
import { createClient } from '@supabase/supabase-js'

/* const supabase = createClient(process.env.SUPABASE_URL, process.env.SUPABASE_KEY) 
 
console.log("Supabase Url : " + process.env.SUPABASE_URL, "Supabase Key : "+ process.env.SUPABASE_KEY) */

const supabase = createClient('https://iqauwajrlxnrpircxpnw.supabase.co', 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImlxYXV3YWpybHhucnBpcmN4cG53Iiwicm9sZSI6ImFub24iLCJpYXQiOjE2NjQ1MjI2MTQsImV4cCI6MTk4MDA5ODYxNH0.i7px1baBwPoRHX0TqCAdGX148mjy6BHk5Wg5wAR6Vbw')

async function signInWithGoogle() {
    const { user, session, error } = await supabase.auth.signInWithOAuth({
        provider: 'google'
    })
    if (error) {
        console.log(error)
        return
    }
    console.log(user, session)
}

async function signInWithFacebook() {
    const { user, session, error } = await supabase.auth.signInWithOAuth({
        provider: 'facebook'
    })
    if (error) {
        console.log(error)
        return
    }
    console.log(user, session)
}

async function signInWithLinkedIn() {
    const { user, session, error } = await supabase.auth.signInWithOAuth({
        provider: 'linkedin'
    })
    if (error) {
        console.log(error)
        return
    }
    console.log(user, session)
}

async function signout() {
    const { error } = await supabase.auth.signOut()
}
</script>
   