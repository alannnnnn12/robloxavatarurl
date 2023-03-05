const express = require('express');
const axios = require('axios');

const app = express();

const ROBLOX_API_ENDPOINT = 'https://thumbnails.roblox.com/v1/users/avatar-headshot';

app.get('/headshot/:userId', async (req, res) => {
  const userId = req.params.userId;
  const size = req.query.size || '420x420';
  const format = req.query.format || 'Png';
  const isCircular = req.query.isCircular || false;

  const url = `${ROBLOX_API_ENDPOINT}?userIds=${userId}&size=${size}&format=${format}&isCircular=${isCircular}`;

  try {
    const response = await axios.get(url, { responseType: 'arraybuffer' });
    res.set('Content-Type', 'image/png');
    res.send(response.data);
  } catch (error) {
    console.error(error);
    res.status(500).send('Error retrieving headshot image');
  }
});

app.listen(3000, () => {
  console.log('Server listening on port 3000');
});
