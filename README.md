# Ml
Ml prototype for BB2

TODO add bias grad
dW2 = np.dot(A1.T, dZ2) / m
db2 = np.sum(dZ2, axis=0, keepdims=True) / m



foreach (var font in new[] { "Consola", "Times"})
            {
                var families = Fonts.GetFontFamilies($@"C:\WINDOWS\Fonts\{font}.TTF");
                foreach (var family in families)
                {
                    var typefaces = family.GetTypefaces();
                    foreach (Typeface typeface in typefaces)
                    {
                        if (typeface.Style != System.Windows.FontStyles.Normal) continue;
                        GlyphTypeface glyph;
                        typeface.TryGetGlyphTypeface(out glyph);
                        IDictionary<int, ushort> characterMap = glyph.CharacterToGlyphMap;
                        using (StreamWriter outputFile = new StreamWriter($"{font}.txt", false, Encoding.ASCII))
                        {
                            using (System.Drawing.FontFamily ff = new System.Drawing.FontFamily(family.FamilyNames[System.Windows.Markup.XmlLanguage.GetLanguage("en-US")]))
                            {
                                foreach (KeyValuePair<int, ushort> kvp in characterMap)
                                {
                                    if (kvp.Key >= Char.MinValue && kvp.Key <= Char.MaxValue)
                                    {
                                        var ch = kvp.Key;


                                        GraphicsPath gp = new GraphicsPath();
                                        gp.AddLine(1, 1, 2, 2);
                                        gp.AddBezier(2, 2, 2, 2,3,3,4,4);
                                        gp.AddBezier(4, 4, 21, 21, 31, 31, 41, 41);

                                        GraphicsPath gp2 = new GraphicsPath();
                                        gp2.AddLine(1, 1, 2, 2);
                                        gp2.AddBezier(2, 2, 2, 2, 3, 3, 4, 4);
                                        gp2.AddBezier(4, 3, 21, 21, 31, 31, 41, 41);

                                        gp.AddString($"{Convert.ToChar(ch)}", ff, (int)System.Drawing.FontStyle.Regular, 1, Point.Empty, fmt);
                                        if (gp.PointCount > 0)
                                        {
                                            outputFile.WriteLine($"{ch} {gp.PointCount}");
                                            for (int i = 0; i < gp.PointCount; i++)
                                            {
                                                outputFile.WriteLine($"{gp.PathPoints[i].X}  {gp.PathPoints[i].Y}    {gp.PathTypes[i]}".Replace(",", "."));
                                            }
                                        }

                                    }

                                }
                            }

                        }

                    }
                }
            }