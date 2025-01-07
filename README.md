# ALLANELLA-MD
Modify your WhatsApp with allanella md
fight for what you need or else you
 going to die with nothing love who loves
 and give shorter distance to your enemies so that you can always have a clue on there next step
case 'play': {
    if (!text) return reply(`*Example*: ${prefix + command} Faded by Alan Walker`);

    try {
       
        await David.sendMessage(m.chat, { react: { text: `🎵`, key: m.key } });

        
        const yts = require("yt-search");
        const search = await yts(text);
        const video = search.videos[0]; 

        if (!video) {
            reply(`*No results found for:* ${text}`);
            return;
        }

        
        const body = `*ALLANELLA-MD_MUSIC - PLAYER*\n` +
                     `> *Title:* ${video.title}\n` +
                     `> *Views:* ${video.views}\n` +
                     `> *Duration:* ${video.timestamp}\n` +
                     `> *Uploaded:* ${video.ago}\n` +
                     `> *Url:* ${video.url}\n` +
                     `> ᴘᴏᴡᴇʀᴇᴅ ʙʏ ᴅᴀᴠɪᴅ ᴄʏʀɪʟ ᴛᴇᴄʜ`;

        await David.sendMessage(m.chat, {
            image: { url: video.thumbnail },
            caption: body
        }, { quoted: m });

        
        const apiUrl = `https://api.allanbenjie.my.id/download/ytmp3?url=${encodeURIComponent(video.url)}`;
        const apiResponse = await axios.get(apiUrl);

        if (apiResponse.data.success) {
            const { download_url, title, thumbnail } = apiResponse.data.result;

      
            await Benjie.sendMessage(m.chat, {
                audio: { url: download_url },
                mimetype: 'audio/mp4',
                fileName: `${title}.mp3`,
                caption: `🎧 *Here's your song:*\n> *Title:* ${title}`
            }, { quoted: m });
        } else {
            reply(`*Failed to fetch the song! Please try again later.*`);
        }
    } catch (error) {
        console.error('Error during /play command:', error);
        reply(`*An error occurred while processing your request. Please try again later.*`);
    }
    break;
}
