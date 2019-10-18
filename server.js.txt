const http = require('http');
const express = require('express');
const app = express();
app.get("/", (request, response) => {
  response.sendStatus(200);
});
app.listen(process.env.PORT);
setInterval(() => {
  http.get(`http://festive-topaz.glitch.me/`);
}, 280000);
 
// ﬂ· «·»ﬂÃ«  «·Ì „„ﬂ‰  Õ ÃÂ« ›Ì «Ì »Ê 
const { Client, RichEmbed } = require("discord.js");
var { Util } = require('discord.js');
const {TOKEN, YT_API_KEY, prefix, devs} = require('./config')
const client = new Client({ disableEveryone: true})
const ytdl = require("ytdl-core");
const canvas = require("canvas");
const Canvas = require("canvas");
const convert = require("hh-mm-ss")
const fetchVideoInfo = require("youtube-info");
const botversion = require('./package.json').version;
const simpleytapi = require('simple-youtube-api')
const moment = require("moment");
const fs = require('fs');
const util = require("util")
const gif = require("gif-search");
const opus = require("node-opus");
const ms = require("ms");
const jimp = require("jimp");
const { get } = require('snekfetch');
const guild = require('guild');
const dateFormat = require('dateformat');//npm i dateformat
const YouTube = require('simple-youtube-api');
const youtube = new YouTube('AIzaSyAdORXg7UZUo7sePv97JyoDqtQVi3Ll0b8');
const hastebins = require('hastebin-gen');
const getYoutubeID = require('get-youtube-id');
const yt_api_key = "AIzaSyDeoIH0u1e72AtfpwSKKOSy3IPp2UHzqi4";
const pretty = require("pretty-ms");
client.login(TOKEN);
const queue = new Map();
var table = require('table').table
const Discord = require('discord.js');
client.on('ready', () => {
  console.log(`Logged in as ${client.user.tag}!`);
});
 
 
 //ﬂÊœ ·· Ã—»…
 
client.on('message', message =>{
  if(message.content === 'Rping'){
let start = Date.now(); message.channel.send('pong').then(message => {
message.edit(`\`\`\`js
Time taken: ${Date.now() - start} ms
Discord API: ${client.ping.toFixed(0)} ms\`\`\``);
  });
  }
});
 
console.log("==================================")
console.log("1")
console.log("2")
console.log("3")
console.log("=========> Bot Online <=========")
console.log("========> TestBot <========")
console.log("=======> Token Bot **** <=======")
console.log("3")
console.log("2")
console.log("1")
console.log("====================================")
console.log("Bot Online 24/7");
 
client.on('message', async msg => {
    if (msg.author.bot) return undefined;
    if (!msg.content.startsWith(prefix)) return undefined;
    const args = msg.content.split(' ');
    const searchString = args.slice(1).join(' ');
    const url = args[1] ? args[1] .replace(/<(.+)>/g, '$1') : '';
    const serverQueue = queue.get(msg.guild.id);
    let command = msg.content.toLowerCase().split(" ")[0];
    command = command.slice(prefix.length)
    if (command === `p`) {
        const voiceChannel = msg.member.voiceChannel;
        if (!voiceChannel) return msg.channel.send('ÌÃ»  Ê¬Ãœ Õ÷— ﬂ »—Ê„ ’Ê Ì .');
        const permissions = voiceChannel.permissionsFor(msg.client.user);
        if (!permissions.has('CONNECT')) {
            return msg.channel.send('·« Ì Ê¬Ãœ ·œÌ ’·«ÕÌ… ·· ﬂ·„ »Â–¬ «·—Ê„');
        }
        if (!permissions.has('SPEAK')) {
            return msg.channel.send('·« Ì Ê¬Ãœ ·œÌ ’·«ÕÌ… ·· ﬂ·„ »Â–¬ «·—Ê„');
        }
 
        if (!permissions.has('EMBED_LINKS')) {
            return msg.channel.sendMessage("**ÌÃ»  Ê¬›— »—„‘‰ `EMBED LINKS`·œÌ **rl")
            }
 
        if (url.match(/^https?:\/\/(www.youtube.com|youtube.com)\/playlist(.*)$/)) {
            const playlist = await youtube.getPlaylist(url);
            const videos = await playlist.getVideos();
            for (const video of Object.values(videos)) {
                const video2 = await youtube.getVideoByID(video.id);
                await handleVideo(video2, msg, voiceChannel, true);
            }
            return msg.channel.send(` **${playlist.title}**  „ «·≈÷¬›… ≈·Ï ﬁ√∆„… «· ‘€Ì·`);
        } else {
            try {
 
                var video = await youtube.getVideo(url);
 
            } catch (error) {
                try {
                                            var fast = {};
                    var videos = await youtube.searchVideos(searchString, 10);
                    let index = 0;
                    const embed1 = new Discord.RichEmbed()
                    .setDescription(`**«·—Ã¬¡ „‰ Õ÷— ﬂ ≈Œ Ì¬— —ﬁ„ «·„ﬁÿ⁄** :
${videos.map(video2 => `[**${++index}**] **${video2.title}**`).join('\n')}`)
                    .setFooter(`${msg.guild.name}`)
                    msg.channel.sendEmbed(embed1).then(message =>{
 
                        message.delete(15000)
 
                    });
                    try {
                        var response = await msg.channel.awaitMessages(msg2 => msg2.content > 0 && msg2.content < 11, {
                            maxMatches: 1,
                            time: 20000,
                            errors: ['time']
                        })
 
                        }catch(err) {
                        console.error(err);
                        return msg.channel.send('·„ Ì „ ≈Œ Ì¬— „ﬁÿ⁄ ’Ê Ì');
                        }
                    const videoIndex = parseInt(response.first().content);
                    var video = await youtube.getVideoByID(videos[videoIndex - 1].id);
                } catch (err) {
                    console.error(err);
                    return msg.channel.send(':x: ·« Ì Ê›— ‰ ¬∆Ã »ÕÀ ');
                }
        }
 
            return handleVideo(video, msg, voiceChannel);
        }
    } else if (command === `sk`) {
        if (!msg.member.voiceChannel) return msg.channel.send('√‰  ·”  »—Ê„ ’Ê Ì .');
        if (!serverQueue) return msg.channel.send('·« Ì Ê›— „ﬁÿ⁄ · Ã¬Ê“Â');
        serverQueue.connection.dispatcher.end(' „  Ã¬Ê“ Â–¬ «·„ﬁÿ⁄');
        return undefined;
    } else if (command === `s`) {
        if (!msg.member.voiceChannel) return msg.channel.send('√‰  ·”  »—Ê„ ’Ê Ì .');
        if (!serverQueue) return msg.channel.send('·« Ì Ê›— „ﬁÿ⁄ ·≈Ìﬁ¬›Â');
        serverQueue.songs = [];
        serverQueue.connection.dispatcher.end(' „ ≈Ìﬁ¬› Â–¬ «·„ﬁÿ⁄');
        return undefined;
    } else if (command === `vol`) {
        if (!msg.member.voiceChannel) return msg.channel.send('√‰  ·”  »—Ê„ ’Ê Ì .');
        if (!serverQueue) return msg.channel.send('·« ÌÊÃœ ‘Ì¡ ‘€¬·.');
        if (!args[1]) return msg.channel.send(`:loud_sound: „” ÊÏ «·’Ê  **${serverQueue.volume}**`);
        serverQueue.volume = args[1];
        serverQueue.connection.dispatcher.setVolumeLogarithmic(args[1] / 50);
        return msg.channel.send(`:speaker:  „  €Ì— «·’Ê  «·Ì **${args[1]}**`);
    } else if (command === `np`) {
        if (!serverQueue) return msg.channel.send('·« ÌÊÃœ ‘Ì¡ Õ«·Ì › «·⁄„·.');
        const embedNP = new Discord.RichEmbed()
    .setDescription(`:notes: «·«‰ Ì „  ‘€Ì· : **${serverQueue.songs[0].title}**`)
        return msg.channel.sendEmbed(embedNP);
    } else if (command === `re`) {
        if (!serverQueue) return msg.channel.send('·« ÌÊÃœ ‘Ì¡ Õ«·Ì › «·⁄„·.');
        const embedNP = new Discord.RichEmbed()
    .setDescription(`”Ì „ «⁄«œÂ  ‘€Ì· «·›œÌÊ :**${serverQueue.songs[0].title}**`)
    msg.channel.send({embed: embedNP})
     return handleVideo(video, msg, msg.member.voiceChannel);
 
    } else if (command === `q`) {
        if (!serverQueue) return msg.channel.send('·« ÌÊÃœ ‘Ì¡ Õ«·Ì › «·⁄„·.');
        let index = 0;
        const embedqu = new Discord.RichEmbed()
.setDescription(`**Songs Queue**
${serverQueue.songs.map(song => `**${++index} -** ${song.title}`).join('\n')}
**«·«‰ Ì „  ‘€Ì·** ${serverQueue.songs[0].title}`)
        return msg.channel.sendEmbed(embedqu);
    } else if (command === `pa`) {
        if (serverQueue && serverQueue.playing) {
            serverQueue.playing = false;
            serverQueue.connection.dispatcher.pause();
            return msg.channel.send(' „ ≈Ìﬁ«› «·„Ê”ÌﬁÏ „ƒﬁ «!');
        }
        return msg.channel.send('·« ÌÊÃœ ‘Ì¡ Õ«·Ì › «·⁄„·.');
    } else if (command === "res") {
        if (serverQueue && !serverQueue.playing) {
            serverQueue.playing = true;
            serverQueue.connection.dispatcher.resume();
            return msg.channel.send('«” √‰›  «·„Ê”ÌﬁÏ »«·‰”»… ·ﬂ !');
        }
        return msg.channel.send('·« ÌÊÃœ ‘Ì¡ Õ«·Ì ›Ì «·⁄„·.');
    }
 
    return undefined;
async function handleVideo(video, msg, voiceChannel, playlist = false) {
    const serverQueue = queue.get(msg.guild.id);
    const song = {
        id: video.id,
        title: Util.escapeMarkdown(video.title),
        url: `https://www.youtube.com/watch?v=${video.id}`,
        time:`${video.duration.hours}:${video.duration.minutes}:${video.duration.seconds}`,
        eyad:`${video.thumbnails.high.url}`,
        best:`${video.channel.title}`,
        bees:`${video.raw.snippet.publishedAt}`,
        shahd:`${video.raw.kind}`,
        zg:`${video.raw.snippet.channelId}`,
        views:`${video.raw.views}`,
        like:`${video.raw.likeCount}`,
        dislike:`${video.raw.dislikeCount}`,
        hi:`${video.raw.id}`
    };
    if (!serverQueue) {
        const queueConstruct = {
            textChannel: msg.channel,
            voiceChannel: voiceChannel,
            connection: null,
            songs: [],
            volume: 5,
            playing: true
        };
        queue.set(msg.guild.id, queueConstruct);
        queueConstruct.songs.push(song);
        try {
            var connection = await voiceChannel.join();
            queueConstruct.connection = connection;
            play(msg.guild, queueConstruct.songs[0]);
        } catch (error) {
            console.error(`I could not join the voice channel: ${error}`);
            queue.delete(msg.guild.id);
            return msg.channel.send(`·« √” ÿÌ⁄ œŒÊ· Â–¬ «·—Ê„ ${error}`);
        }
    } else {
        serverQueue.songs.push(song);
        console.log(serverQueue.songs);
        if (playlist) return undefined;
        else return msg.channel.send(` **${song.title}**  „ «÷«›Â «·«€‰Ì… «·Ì «·ﬁ«∆„…!`);
    }
    return undefined;
}
 
function play(guild, song) {
    const serverQueue = queue.get(guild.id);
 
    if (!song) {
        serverQueue.voiceChannel.leave();
        queue.delete(guild.id);
        return;
    }
    console.log(serverQueue.songs);
    const dispatcher = serverQueue.connection.playStream(ytdl(song.url))
        .on('end', reason => {
            if (reason === ' Ì«— ·« ÌÊ·œ »”—⁄… ﬂ«›Ì….') console.log('Song ended.');
            else console.log(reason);
            serverQueue.songs.shift();
            play(guild, serverQueue.songs[0]);
        })
        .on('error', error => console.error(error));
    dispatcher.setVolumeLogarithmic(serverQueue.volume / 5);
        fetchVideoInfo(`${song.hi}`, function (err,  idk) {
  if (err) throw new Error(err);
  console.log( idk);
      const yyyy = {}
  if(!yyyy[msg.guild.id]) yyyy[msg.guild.id] = {
    like: `${ idk.likeCount}`,
    dislike: `${ idk.dislikeCount}`
  }
    serverQueue.textChannel.send({embed : new Discord.RichEmbed()
  .setTitle(`**${ idk.title}**`)
  .setURL( idk.url)
  .addField('Time The Video :' , `${song.time}`, true)
  .addField('Channel Name :' , `${song.best}`, true)
  .addField('Channel ID :' , `${song.zg}`, true)
  .addField('Video Created at :' , `${ idk.datePublished}`, true)
  .addField('Views :' , `${ idk.views}`, true)
  .addField('Like?? :' , `${ idk.likeCount}`, true)
  .addField('dislike?? :' , `${ idk.dislikeCount}`, true)
  .addField('comments :' , `${ idk.commentCount}`, true)
    .setImage(`${song.eyad}`)
    .setThumbnail('http://cdn.akhbaar24.com/430e061a-f89a-43c7-86d9-82fae5f7c495.jpg')
    .setColor('#ff0000')
    .setTimestamp()
    }).then(love => {
        love.react('??').then(r=>{
        love.react('??').then(r =>{
        love.react('??').then(r=> {
    let likee = (reaction, user) => reaction.emoji.name === '??' && user.id === msg.author.id;
    let dislikee = (reaction, user) => reaction.emoji.name === '??' && user.id === msg.author.id;
    let cnn = (reaction, user) => reaction.emoji.name === '??' && user.id === msg.author.id;
 
    let ll = love.createReactionCollector(likee , {max:5});
    let dd = love.createReactionCollector(dislikee , {max:5});
    let cn = love.createReactionCollector(cnn , {max:5});
 
            ll.on("collect", r => {
              yyyy[msg.guild.id].like++;
    love.edit({embed : new Discord.RichEmbed()
  .setTitle(`**${ idk.title}**`)
  .setURL( idk.url)
  .addField('Time The Video :' , `${song.time}`, true)
  .addField('Channel Name :' , `${song.best}`, true)
  .addField('Channel ID :' , `${song.zg}`, true)
  .addField('Video Created at :' , `${ idk.datePublished}`, true)
  .addField('Views :' , `${ idk.views}`, true)
  .addField('Like?? :' , `${yyyy[msg.guild.id].like}`, true)
  .addField('dislike?? :' , `${ idk.dislikeCount}`, true)
  .addField('comments :' , `${ idk.commentCount}`, true)
    .setImage(`${song.eyad}`)
    .setThumbnail('http://cdn.akhbaar24.com/430e061a-f89a-43c7-86d9-82fae5f7c495.jpg')
    .setColor('#ff0000')
    .setTimestamp()
});
    })
 
    dd.on("collect", r => {
      yyyy[msg.guild.id].dislike++;
    love.edit({embed : new Discord.RichEmbed()
  .setTitle(`**${ idk.title}**`)
  .setURL( idk.url)
  .addField('Time The Video :' , `${song.time}`, true)
  .addField('Channel Name :' , `${song.best}`, true)
  .addField('Channel ID :' , `${song.zg}`, true)
  .addField('Video Created at :' , `${ idk.datePublished}`, true)
  .addField('Views :' , `${ idk.views}`, true)
  .addField('Like?? :' , `${ idk.likeCount}`, true)
  .addField('dislike?? :' , `${yyyy[msg.guild.id].dislike}`, true)
  .addField('comments :' , `${ idk.commentCount}`, true)
    .setImage(`${song.eyad}`)
    .setThumbnail('http://cdn.akhbaar24.com/430e061a-f89a-43c7-86d9-82fae5f7c495.jpg')
    .setColor('#ff0000')
    .setTimestamp()
});
})
    cn.on("collect", r => {
    love.edit({embed : new Discord.RichEmbed()
  .setTitle(`**${ idk.title}**`)
  .setURL( idk.url)
  .addField('Time The Video :' , `${song.time}`, true)
  .addField('Channel Name :' , `${song.best}`, true)
  .addField('Channel ID :' , `${song.zg}`, true)
  .addField('Video Created at :' , `${ idk.datePublished}`, true)
  .addField('Views :' , `${ idk.views}`, true)
  .addField('Like?? :' , `${ idk.likeCount}`, true)
  .addField('dislike?? :' , `${ idk.dislikeCount}`, true)
  .addField('comments :' , `${ idk.commentCount}`, true)
    .setImage(`${song.eyad}`)
    .setThumbnail('http://cdn.akhbaar24.com/430e061a-f89a-43c7-86d9-82fae5f7c495.jpg')
    .setColor('#ff0000')
    .setTimestamp()
});
})
})
})
})
})
})
}
});
 
client.on('ready', function(){
    var ms = 5000 ;
    var setGame = [`${prefix}help`];
    var i = -1;
    var j = 0;
    setInterval(function (){
        if( i == -1 ){
            j = 1;
        }
        if( i == (setGame.length)-1 ){
            j = -1;
        }
        i = i+j;
        client.user.setGame(setGame[i],`http://www.twitch.tv/imd3s_x`);
    }, ms);30000
 
});
 
client.on("message", message => {
    if (message.content === (prefix + "help")) {
     const embed = new Discord.RichEmbed()
         .setColor("#580e6b")
         .setThumbnail(message.author.avatarURL)
         .setDescription(`***
         
          «Ê«„—  ‘€Ì· «·„ÌÊ“ﬂ
              
${prefix}5p ==== > · ‘€Ì· «·«€‰Ì…
${prefix}s ==== > ·«Ìﬁ«› Ã„Ì⁄ «·«€«‰Ì
${prefix}sk ==== > · ŒÿÌ «·«€‰Ì…
${prefix}vol ==== > ·—›⁄ «Ê Œ›÷ «·’Ê 
${prefix}np ==== > ·⁄—÷ «·«€‰Ì… «· Ì Ì „  ‘€Ì·Â«
${prefix}re ==== > ·«⁄«œ…  ‘€Ì· «·«€‰Ì…
${prefix}q ==== > ·⁄—÷ ﬁ«∆„… «· ‘€Ì·
${prefix}pa ==== > ·«Ìﬁ«› «·«€‰Ì… «·„‘ €·…
       ***`)
 
   message.author.sendEmbed(embed)
   
   }
   });